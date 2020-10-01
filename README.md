# zha-network-visualization-card
Lovelace custom element for visualizing the ZHA Zigbee network

[zha-map](https://github.com/zha-ng/zha-map) integration commponent for [Home Assistant](https://www.home-assistant.io) allow you to make a ZHA (Zigbee Home Automation) network topology map and zha-network-visualization-card allows you to visualize that map in Lovelace.

Requires that you are already using the [ZHA](https://www.home-assistant.io/integrations/zha/) integration commponent in Home Assistant.

Zigbee network mapping with zha-map can help you identify weak points like bad links between your devices.

# Installation Instructions

1. Install the zha_map custom component
- https://github.com/zha-ng/zha-map
2. Add zha_map: to your configuration.yaml and restart Home Assistant
3. Wait for a scan to complete (logs to DEBUG, or use the new zha_map service to scan on demand)
4. Put the [zha-network-visualization-card.js](https://github.com/dmulcahey/zha-network-visualization-card) lovelace card into the `\[config\]/www/zha-network-visualization-card directory` ether by copying it there or by using the file editor to create it with a cut and paste of the content.
5. Add the lovelace resource with `Configuration ¦ Lovelace Dashboards ¦ Resources ¦ ⊕ ¦ URL:/local/zha-network-visualization-card/zha-network-visualization-card.js` & `Resource Type JavaScript Module ¦ Update`.
6. Add custom card (works best in panel mode) through `Overview ¦ ⋮ ¦ Configure UI ¦ New Tab + ¦ Give it a Title and any other options` & `select Panel Mode`. Open this new view which will be empty, at the bottom right click the + for cards window. Choose the manual card type and a card configuration window will open, this is where you will add type: `custom:zha-network-visualization-card`. Save and exit UI configurator
7. Optional: Restart Home Assistant. Once its back go to Developer Tools then open the Services tab and choose the `zha_map.scan_now` service and click call service button. Check logs for details.

New map card should be there.

# Usage
The Zigbee coordinator will be represented by a rectangle at the top. Any device that serves as Zigbee router (usually all devices running on Mains electricity / grid power) will represented as ovals, and Zigbee end-device (usually battery powered sensors) will be represented by as circles.

The lines between those representions show all the possible paths through Zigbee mesh. Any path with a LQI over 192 is shown as green, LQI 129-192 is shown as yellow, and anything 128 and lower is shown as red.

# Related projects

### zha-map
**[zha-map](https://github.com/zha-ng/zha-map)** integration commponent for [Home Assistant](https://www.home-assistant.io) allow you to make a ZHA (Zigbee Home Automation) network topology map. **zha-network-visualization-card** relies on this data to visualize that map in Lovelace of Zigbee devices and the connections between them.

### Zigzag
**[Zigzag](https://github.com/Samantha-uk/zigzag)** is an alternative custom card/panel for [Home Assistant](https://www.home-assistant.io/) that displays a graphical layout of Zigbee devices and the connections between them. Zigzag can be installed as a panel or a custom card and relies on the data provided by the [zha-map](https://github.com/zha-ng/zha-map) integration commponent. Like zha-network-visualization-card, Zigzag also relies on the data provided by the [zha-map](https://github.com/zha-ng/zha-map) integration commponent.

#### ZHA Network Card
[zha-network-card](https://github.com/dmulcahey/zha-network-card) is a another alternative custom Lovelace card for Home Assistant that displays ZHA component Zigbee network and device information in Home Assistant. This implementation leverages the ZHA websocket API to get ZHA device information instead.

#### ZHA Device Exporter
[zha-device-exporter](https://github.com/dmulcahey/zha-device-exporter) is a custom component for Home Assistant to allow the ZHA component to export lists of Zigbee devices.

### Zigpy
**[zigpy](https://github.com/zigpy/zigpy)** is [Zigbee protocol stack](https://en.wikipedia.org/wiki/Zigbee) integration project to implement the **[Zigbee Home Automation](https://www.zigbee.org/)** standard as a Python library. Zigbee Home Automation integration with zigpy allows you to connect one of many off-the-shelf Zigbee adapters using one of the available Zigbee radio library modules compatible with zigpy to control Zigbee devices. There is currently support for controlling Zigbee device types such as binary sensors (e.g. motion and door sensors), analog sensors (e.g. temperature sensors), lightbulbs, switches, and fans. Zigpy is tightly integrated with [Home Assistant](https://www.home-assistant.io)'s [ZHA component](https://www.home-assistant.io/components/zha/) and provides a user-friendly interface for working with a Zigbee network.
