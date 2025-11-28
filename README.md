# 🤩 🤩 🤩 COMP0221 MQTT Visualiser 🤩 🤩 🤩

This project provides a Python-based visualiser for the COMP0221 coursework. It subscribes to an MQTT topic, validates incoming data packets, and displays the state of the flock in a 3D plot.

## Running the Visualiser

To run the visualiser, simply execute the Python script. You do not need to do any configuration.

```bash
python3 visualiser.py
```

## Dependencies

Install dependencies:

```bash
pip install -r requirements.txt
```

## MQTT Configuration

The visualiser connects to a public MQTT broker with the following details:

- **Broker URI**: `mqtt://broker.hivemq.com`
- **Topic**: `flocksim`

## Expected Payload Format

The visualiser expects incoming messages on the `flocksim` topic to be JSON objects with the following structure. This format is defined in the COMP0221 Standard document.

```
{
    "version":      <integer>,
    "team_id":      <integer>,
    "node_id":      <string>,
    "seq_number":   <integer>,
    "ts_s":         <integer>,
    "ts_ms":        <integer>,
    "x_mm":         <integer>,
    "y_mm":         <integer>,
    "z_mm":         <integer>,
    "vx_mm_s":      <integer>,
    "vy_mm_s":      <integer>,
    "vz_mm_s":      <integer>,
    "yaw_cd":       <integer>,
    "mac_tag":      <string>
}
```

### MAC Tag Calculation

The `mac_tag` is the **last** 4 bytes of an AES-128 CMAC calculated over the shared struct as described in the COMP0221 standard. The visualiser uses a shared key to verify the integrity of the payload.

- **Shared Key**: `2B7E151622A0D2A6ACF7198809CF4F3C`

## Adding your MAC address and name

You can add your MAC address and name to the dictionary defined in `mac_dict.py`.
