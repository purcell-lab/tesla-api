# Energy State

These endpoints are not yet documented.

| Cmd | Endpoint                |
| :-- | :---------------------- |
| GET | `savings_forecast`      |
| GET | `backup_time_remaining` |

## GET `/api/1/energy_sites/{site_id}/live_status`

Retrieves current system information (e.g. solar production, grid export/import, home consumption, etc.).

### Response for solar panel system without powerwalls

```json
{
  "response": {
    "solar_power": 7720,
    "energy_left": 0,
    "total_pack_energy": 1,
    "percentage_charged": 0,
    "battery_power": 0,
    "load_power": 4517.14990234375,
    "grid_status": "Unknown",
    "grid_services_active": false,
    "grid_power": -3202.85009765625,
    "grid_services_power": 0,
    "generator_power": 0,
    "island_status": "island_status_unknown",
    "storm_mode_active": false,
    "timestamp": "2022-07-28T17:11:27Z",
    "wall_connectors": null
  }
}
```

## GET `/api/1/energy_sites/{site_id}/site_status`

Retrieves general system information.

### Response for solar panel system without powerwalls

```json
{
  "response": {
    "resource_type": "solar",
    "asset_site_id": "47d04752-9cf1-4e76-88fb-08839a1c41c4",
    "solar_power": 7700,
    "solar_type": "pv_panel",
    "storm_mode_enabled": null,
    "powerwall_onboarding_settings_set": null,
    "sync_grid_alert_enabled": false,
    "breaker_alert_enabled": false
  }
}
```

## GET `/api/1/energy_sites/{site_id}/site_info`

Retrieves general system information.

### Response for solar panel system without powerwalls

```json
{
  "response": {
    "id": "313dbc37-555c-45b1-83aa-62a4ef9ff7ac",
    "site_name": "My House",
    "site_number": "2252147638651575",
    "installation_date": "2022-04-04T15:56:35-07:00",
    "user_settings": {
      "storm_mode_enabled": null,
      "powerwall_onboarding_settings_set": null,
      "sync_grid_alert_enabled": false,
      "breaker_alert_enabled": false
    },
    "components": {
      "solar": true,
      "solar_type": "pv_panel",
      "battery": false,
      "grid": true,
      "backup": false,
      "gateway": "gateway_type_none",
      "load_meter": true,
      "tou_capable": false,
      "storm_mode_capable": false,
      "flex_energy_request_capable": false,
      "car_charging_data_supported": false,
      "off_grid_vehicle_charging_reserve_supported": false,
      "vehicle_charging_performance_view_enabled": false,
      "vehicle_charging_solar_offset_view_enabled": false,
      "battery_solar_offset_view_enabled": false,
      "energy_service_self_scheduling_enabled": true,
      "rate_plan_manager_supported": true,
      "configurable": false,
      "grid_services_enabled": false
    },
    "installation_time_zone": "America/Los_Angeles",
    "time_zone_offset": -420,
    "geolocation": {
      "latitude": 32.53452700000001,
      "longitude": -112.3463137
    },
    "address": {
      "address_line1": "1234 Tesla Solar Ave",
      "city": "Austin",
      "state": "TX",
      "zip": "123456",
      "country": "US"
    }
  }
}
```

## GET `/api/1/energy_sites/{site_id}/tariff_rates`

Same as `rate_tarrifs` below.

## GET `/api/1/energy_sites/rate_tariffs`

Retrieves tarriff IDs for utility companies. Only 4 of the 233 entries are shown below.

### Response for solar panel system without powerwalls

```json
{
  "response": [
    {
      "tariffID": "AE-R-CS",
      "description": "Residential - Community Solar",
      "utility": "Austin Energy",
      "country": "US",
      "state": "TX"
    },
    {
      "tariffID": "AE-R-VOS",
      "description": "Residential - Value of Solar",
      "utility": "Austin Energy",
      "country": "US",
      "state": "TX"
    },
    {
      "tariffID": "APS-ET-1",
      "description": "Residential - Time of Use, Time Advantage, 9pm - 9 am",
      "utility": "Arizona Public Service Co",
      "country": "US",
      "state": "AZ"
    },
    {
      "tariffID": "XCEL-RE-TOU",
      "description": "Residential - Energy, Time of Use",
      "utility": "Xcel Energy - Colorado",
      "country": "US",
      "state": "CO"
    }
  ],
  "count": 233
}
```

## GET `/api/1/energy_sites/{site_id}/programs`

Retrieves energy site program information.

### Response for solar panel system without powerwalls

```json
{
  "response": {
    "programs": []
  }
}
```

## GET `api/1/energy_sites/{site_id}/tariff_rate`

Retrieves the user defined Utility Rate Plan used for Time-Based Control mode.
It looks like this endpoint is updated every 30 minutes.

```json
{
    "response": {
        "name": "Amber",
        "utility": "Amber",
        "daily_charges": [
            {
                "amount": 0,
                "name": "Charge"
            }
        ],
        "demand_charges": {
            "ALL": {
                "ALL": 0
            },
            "Summer": {},
            "Winter": {}
        },
        "energy_charges": {
            "ALL": {
                "ALL": 0
            },
            "Summer": {
                "ON_PEAK": 0.43,
                "PARTIAL_PEAK": 0.43,
                "OFF_PEAK": 0.01
            },
            "Winter": {}
        },
        "seasons": {
            "Summer": {
                "fromDay": 1,
                "toDay": 31,
                "fromMonth": 1,
                "toMonth": 12,
                "tou_periods": {
                    "ON_PEAK": [
                        {
                            "fromDayOfWeek": 0,
                            "toDayOfWeek": 6,
                            "fromHour": 5,
                            "fromMinute": 30,
                            "toHour": 7,
                            "toMinute": 0
                        },
                        {
                            "fromDayOfWeek": 0,
                            "toDayOfWeek": 6,
                            "fromHour": 17,
                            "fromMinute": 0,
                            "toHour": 20,
                            "toMinute": 0
                        }
                    ],
                    "PARTIAL_PEAK": [
                        {
                            "fromDayOfWeek": 0,
                            "toDayOfWeek": 6,
                            "fromHour": 7,
                            "fromMinute": 0,
                            "toHour": 10,
                            "toMinute": 0
                        },
                        {
                            "fromDayOfWeek": 0,
                            "toDayOfWeek": 6,
                            "fromHour": 15,
                            "fromMinute": 0,
                            "toHour": 17,
                            "toMinute": 0
                        }
                    ],
                    "OFF_PEAK": [
                        {
                            "fromDayOfWeek": 0,
                            "toDayOfWeek": 6,
                            "fromHour": 10,
                            "fromMinute": 0,
                            "toHour": 10,
                            "toMinute": 30
                        },
                        {
                            "fromDayOfWeek": 0,
                            "toDayOfWeek": 6,
                            "fromHour": 10,
                            "fromMinute": 30,
                            "toHour": 15,
                            "toMinute": 0
                        },
                        {
                            "fromDayOfWeek": 0,
                            "toDayOfWeek": 6,
                            "fromHour": 20,
                            "fromMinute": 0,
                            "toHour": 5,
                            "toMinute": 30
                        }
                    ]
                }
            },
            "Winter": {
                "fromDay": 0,
                "toDay": 0,
                "fromMonth": 0,
                "toMonth": 0,
                "tou_periods": {}
            }
        },
        "sell_tariff": {
            "name": "Amber",
            "utility": "Amber",
            "daily_charges": [
                {
                    "amount": 0,
                    "name": "Charge"
                }
            ],
            "demand_charges": {
                "ALL": {
                    "ALL": 0
                },
                "Summer": {},
                "Winter": {}
            },
            "energy_charges": {
                "ALL": {
                    "ALL": 0
                },
                "Summer": {
                    "ON_PEAK": 0.3,
                    "PARTIAL_PEAK": 0.1,
                    "OFF_PEAK": 0.01
                },
                "Winter": {}
            },
            "seasons": {
                "Summer": {
                    "fromDay": 1,
                    "toDay": 31,
                    "fromMonth": 1,
                    "toMonth": 12,
                    "tou_periods": {
                        "ON_PEAK": [
                            {
                                "fromDayOfWeek": 0,
                                "toDayOfWeek": 6,
                                "fromHour": 5,
                                "fromMinute": 30,   
                                "toHour": 7,
                                "toMinute": 0
                            },
                            {
                                "fromDayOfWeek": 0,
                                "toDayOfWeek": 6,
                                "fromHour": 17,
                                "fromMinute": 0,
                                "toHour": 20,
                                "toMinute": 0
                            }
                        ],
                        "PARTIAL_PEAK": [
                            {
                                "fromDayOfWeek": 0,
                                "toDayOfWeek": 6,
                                "fromHour": 7,
                                "fromMinute": 0,
                                "toHour": 10,
                                "toMinute": 0
                            },
                            {
                                "fromDayOfWeek": 0,
                                "toDayOfWeek": 6,
                                "fromHour": 15,
                                "fromMinute": 0,
                                "toHour": 17,
                                "toMinute": 0
                            }
                        ],
                        "OFF_PEAK": [
                            {
                                "fromDayOfWeek": 0,
                                "toDayOfWeek": 6,
                                "fromHour": 10,
                                "fromMinute": 0,
                                "toHour": 10,
                                "toMinute": 30
                            },
                            {
                                "fromDayOfWeek": 0,
                                "toDayOfWeek": 6,
                                "fromHour": 10,
                                "fromMinute": 30,
                                "toHour": 15,
                                "toMinute": 0
                            },
                            {
                                "fromDayOfWeek": 0,
                                "toDayOfWeek": 6,
                                "fromHour": 20,
                                "fromMinute": 0,
                                "toHour": 5,
                                "toMinute": 30
                            }
                        ]
                    }
                },
                "Winter": {
                    "fromDay": 0,
                    "toDay": 0,
                    "fromMonth": 0,
                    "toMonth": 0,
                    "tou_periods": {}
                }
            }
        }
    }
}                            
