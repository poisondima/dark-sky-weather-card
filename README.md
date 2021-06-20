# Dark Sky Weather Card для Home Assistant

![screen_from_ha](https://user-images.githubusercontent.com/39500249/122648984-533ddd80-d134-11eb-8aff-48fa24265ee2.png)

Оригинальный репозиторий https://github.com/iammexx/home-assistant-config/tree/master/ui/darksky, но он не обновляется с 2019 года.

## Установка
Добавляем в сенсоры сервис Dark Sky:
```yaml
  - platform: darksky
    api_key: !secret darksky_api_key
    forecast:
      - 0
      - 1
      - 2
      - 3
      - 4
      - 5
    language: ru
    monitored_conditions:
      - icon
      - summary
      - nearest_storm_distance
      - nearest_storm_bearing
      - humidity
      - temperature
      - temperature_high
      - temperature_low
      - apparent_temperature
      - apparent_temperature_high
      - apparent_temperature_low
      - wind_speed
      - wind_bearing
      - precip_type
      - precip_probability
      - precip_accumulation
      - precip_intensity
      - precip_intensity_max
      - uv_index
      - daily_summary
      - pressure
      - visibility
```
Перезагружаем HA и проверяем, что появились сенсоры `sensor.dark_sky_*`

Устанавливаем через HACS карточку:
> HACS > Пользовательский интерфейс > 3 точки (правый верхний угол) > Пользовательские репозитории > URL: `poisondima/dark-sky-weather-card`, Категория: Lovelace > Добавить > Выбираем в списке > Dark Sky Weather Card > Жмем Установить

Добавляем в ui-lovelace:
```yaml
  - type: 'custom:dark-sky-weather-card'
    entity_current_conditions: sensor.dark_sky_icon
    entity_temperature: sensor.dark_sky_temperature
    entity_forecast_high_temp_1: sensor.dark_sky_daytime_high_temperature_1d
    entity_forecast_high_temp_2: sensor.dark_sky_daytime_high_temperature_2d
    entity_forecast_high_temp_3: sensor.dark_sky_daytime_high_temperature_3d
    entity_forecast_high_temp_4: sensor.dark_sky_daytime_high_temperature_4d
    entity_forecast_high_temp_5: sensor.dark_sky_daytime_high_temperature_5d
    entity_forecast_icon_1: sensor.dark_sky_icon_1d
    entity_forecast_icon_2: sensor.dark_sky_icon_2d
    entity_forecast_icon_3: sensor.dark_sky_icon_3d
    entity_forecast_icon_4: sensor.dark_sky_icon_4d
    entity_forecast_icon_5: sensor.dark_sky_icon_5d
    entity_forecast_low_temp_1: sensor.dark_sky_overnight_low_temperature_0d
    entity_forecast_low_temp_2: sensor.dark_sky_overnight_low_temperature_1d
    entity_forecast_low_temp_3: sensor.dark_sky_overnight_low_temperature_2d
    entity_forecast_low_temp_4: sensor.dark_sky_overnight_low_temperature_3d
    entity_forecast_low_temp_5: sensor.dark_sky_overnight_low_temperature_4d
    entity_summary_1: sensor.dark_sky_summary_1d
    entity_summary_2: sensor.dark_sky_summary_2d
    entity_summary_3: sensor.dark_sky_summary_3d
    entity_summary_4: sensor.dark_sky_summary_4d
    entity_summary_5: sensor.dark_sky_summary_5d
    entity_sun: sun.sun
    entity_visibility: sensor.dark_sky_visibility
    entity_daytime_high: sensor.dark_sky_daytime_high_temperature_0d
    entity_wind_bearing: sensor.dark_sky_wind_bearing
    entity_wind_speed: sensor.dark_sky_wind_speed
    entity_humidity: sensor.dark_sky_humidity
    entity_pressure: sensor.dark_sky_pressure
    entity_apparent_temp: sensor.dark_sky_apparent_temperature
    entity_daily_summary: sensor.dark_sky_daily_summary
    entity_pop: sensor.dark_sky_precip_probability
    entity_pop_intensity: sensor.dark_sky_precip_intensity
    entity_pop_1: sensor.dark_sky_precip_probability_1d
    entity_pop_2: sensor.dark_sky_precip_probability_2d
    entity_pop_3: sensor.dark_sky_precip_probability_3d
    entity_pop_4: sensor.dark_sky_precip_probability_4d
    entity_pop_5: sensor.dark_sky_precip_probability_5d
    locale: ru
```
