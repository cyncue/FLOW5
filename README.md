# FLOW5
ESTE REPOSITORIO MUESTRA EL CONTROL DE TEMPERATURA Y MANDA NOTIFICACION

[
    {
        "id": "aea0ddd0260a1dd6",
        "type": "tab",
        "label": "Flow 5",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "6c19f3d51ee01d7d",
        "type": "mqtt in",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "topic": "capstone/team15/command",
        "qos": "2",
        "datatype": "auto-detect",
        "broker": "ecd64a3cd51ca71d",
        "nl": false,
        "rap": true,
        "rh": 0,
        "inputs": 0,
        "x": 200,
        "y": 80,
        "wires": [
            [
                "ce28f82839677cb5",
                "ac619b0493d5ff26",
                "397d972310ba2d1d"
            ]
        ]
    },
    {
        "id": "397d972310ba2d1d",
        "type": "switch",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "property": "payload",
        "propertyType": "msg",
        "rules": [
            {
                "t": "gt",
                "v": "33",
                "vt": "num"
            },
            {
                "t": "lt",
                "v": "30",
                "vt": "num"
            },
            {
                "t": "else"
            }
        ],
        "checkall": "true",
        "repair": false,
        "outputs": 3,
        "x": 170,
        "y": 160,
        "wires": [
            [
                "b6a8e82ba06a31e7"
            ],
            [
                "5cc8d19792802e4f"
            ],
            [
                "a5567e58bd867819"
            ]
        ]
    },
    {
        "id": "b6a8e82ba06a31e7",
        "type": "change",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "la temperatura del contenedor es muy alta",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 340,
        "y": 140,
        "wires": [
            [
                "3b7b2c5f21398524"
            ]
        ]
    },
    {
        "id": "5cc8d19792802e4f",
        "type": "change",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "la temoeratura del contenedor es muy baja",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 340,
        "y": 180,
        "wires": [
            [
                "3b7b2c5f21398524"
            ]
        ]
    },
    {
        "id": "a5567e58bd867819",
        "type": "change",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "todo ok",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 340,
        "y": 220,
        "wires": [
            [
                "3b7b2c5f21398524"
            ]
        ]
    },
    {
        "id": "3b7b2c5f21398524",
        "type": "rbe",
        "z": "aea0ddd0260a1dd6",
        "name": "rbe",
        "func": "rbe",
        "gap": "",
        "start": "",
        "inout": "out",
        "septopics": false,
        "property": "payload",
        "topi": "topic",
        "x": 510,
        "y": 180,
        "wires": [
            [
                "a5f14428b5609310",
                "be83981a4a2cf729",
                "071ffe3ddc707a28"
            ]
        ]
    },
    {
        "id": "071ffe3ddc707a28",
        "type": "e-mail",
        "z": "aea0ddd0260a1dd6",
        "server": "smtp.gmail.com",
        "port": "465",
        "secure": true,
        "tls": true,
        "name": "cynthia.cuellar@uppuebla.edu.mx",
        "dname": "",
        "x": 780,
        "y": 320,
        "wires": []
    },
    {
        "id": "a5f14428b5609310",
        "type": "ui_text",
        "z": "aea0ddd0260a1dd6",
        "group": "86e1f10557cab5ed",
        "order": 1,
        "width": 0,
        "height": 0,
        "name": "",
        "label": "contenedor",
        "format": "{{msg.payload}}",
        "layout": "row-spread",
        "className": "",
        "x": 690,
        "y": 220,
        "wires": []
    },
    {
        "id": "ac619b0493d5ff26",
        "type": "ui_gauge",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "group": "86e1f10557cab5ed",
        "order": 0,
        "width": 0,
        "height": 0,
        "gtype": "gage",
        "title": "gauge",
        "label": "units",
        "format": "{{value}}",
        "min": 0,
        "max": 10,
        "colors": [
            "#00b500",
            "#e6e600",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "className": "",
        "x": 650,
        "y": 120,
        "wires": []
    },
    {
        "id": "ce28f82839677cb5",
        "type": "debug",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 630,
        "y": 60,
        "wires": []
    },
    {
        "id": "be83981a4a2cf729",
        "type": "debug",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 690,
        "y": 260,
        "wires": []
    },
    {
        "id": "ecd64a3cd51ca71d",
        "type": "mqtt-broker",
        "name": "HIVEMQ",
        "broker": "broker.hivemq.com",
        "port": "1883",
        "clientid": "",
        "autoConnect": true,
        "usetls": false,
        "protocolVersion": "4",
        "keepalive": "60",
        "cleansession": true,
        "birthTopic": "",
        "birthQos": "0",
        "birthPayload": "",
        "birthMsg": {},
        "closeTopic": "",
        "closeQos": "0",
        "closePayload": "",
        "closeMsg": {},
        "willTopic": "",
        "willQos": "0",
        "willPayload": "",
        "willMsg": {},
        "userProps": "",
        "sessionExpiry": ""
    },
    {
        "id": "86e1f10557cab5ed",
        "type": "ui_group",
        "name": "temperature",
        "tab": "7f7bc8ca7693921c",
        "order": 1,
        "disp": true,
        "width": "6",
        "collapse": false,
        "className": ""
    },
    {
        "id": "7f7bc8ca7693921c",
        "type": "ui_tab",
        "name": "command",
        "icon": "dashboard",
        "disabled": false,
        "hidden": false
    }
]
