# tesla_ev

FiveM Electric Vehicle HUD, battery, charging, garage-charging

This resource was created for demonstration purposes. Some features are basic, like `garagedemo`, and all scripts are client side.

In the future these may be integrated into frameworks and/or include their own server side/persistence logic.

- EV HUD
    - EV vehicles display Whr (watt-hours) energy use
    - This figure is based on "RPMs" and Whr effects battery range
- EV Battery
    - EV vehicles have batteries instead of fuel
    - The battery discharge loosely follows real-life heuristics
        - A HUD is rendered on the minimap showing charge level %
        - Discharging uses a stepping function based on "RPM"
            - High RPMs (e.g. racing) will negatively effect range
            - Low RPMs benefit from less energy use
- EV Charger
    - Featuring the Tesla Supercharger 3D model
        - Via an included custom map: `tesla_supercharger`
    - Charging uses a quadratic Bezier curve
        - 0-60% takes ~30% of total charge time
        - &gt;61% takes the remaining time to reach full charge
    - Supports custom charging rates via `config.lua`
- Garage Demo
    - Mostly for demonstration purposes
    - Adds the concept of charging while your vehicle is stored in a garage
    - Supports custom charging rates via `config.lua`
        - Example: parking-garages charge faster than parking lots, which are faster than house-garages

## Requirements

 - [tesla_redis](https://github.com/Boostvolt/tesla_redis)
    - The `garagedemo/config.lua` offers the ability switch between in-memory (client) persistence and actual persistence using our [tesla_redis](https://github.com/Boostvolt/tesla_redis) library.
    - The default configuration is to use in-memory, but if you want to test out [tesla_redis](https://github.com/Boostvolt/tesla_redis), have a Redis server running on the same machine as the host.
    - Changing `Config.Garage.DB = DB.Client` to `Config.Garage.DB = DB.Redis` will switch the persitence method.
    - [tesla_redis](https://github.com/Boostvolt/tesla_redis) is in early development, currently expects the server to be at `127.0.0.1:6379`. The ability to configure [tesla_redis](https://github.com/Boostvolt/tesla_redis), and change this, is in the works. 
    
## Chargeable cars
- [Tesla Model S](https://github.com/boostvolt/tesla_models)
- [Tesla Model X](https://github.com/boostvolt/tesla_modelx)
- [Tesla Model 3](https://github.com/boostvolt/tesla_model3)
- [Tesla Model Y](https://github.com/boostvolt/tesla_model3)
- [Tesla Cybertruck](https://github.com/boostvolt/tesla_cybertruck)
- [Tesla Roadster](https://github.com/boostvolt/tesla_roadster)
- [Tesla Semi](https://github.com/boostvolt/tesla_semi)

## Download

This resource was developed alongside [tesla_redis](https://github.com/Boostvolt/tesla_redis). This resource will not work without them, so you will need to install them as well.

### Using Git
```
cd resources
git clone https://github.com/boostvolt/tesla_ev [tesla]/tesla_ev/
```

### Manually
- Download https://github.com/boostvolt/tesla_ev/archive/master.zip
- Create and place in in `[tesla]/tesla_ev` directory

## Installation
- Add this in your `server.cfg`:

```lua
start tesla_ev
```

## Debug
- Debug commands available when `Config.Debug = True`
- `/modelx` spawns and places you in the Tesla Model X
- `/charge 40` will set fuel to specified amount (40 as an example)

## Screenshots

![photo_2019-04-14_00-43-29 (5)](https://user-images.githubusercontent.com/79330/56089919-310eed80-5e4f-11e9-9fd1-fa0eb3027122.jpg)

![photo_2019-04-14_00-43-29 (6)](https://user-images.githubusercontent.com/79330/56089925-3a985580-5e4f-11e9-9ff3-eb9430e0fbaf.jpg)

![photo_2019-04-14_00-43-29 (4)](https://user-images.githubusercontent.com/79330/56089926-3f5d0980-5e4f-11e9-8809-cf90160ba203.jpg)

![photo_2019-04-14_00-43-29 (3)](https://user-images.githubusercontent.com/79330/56089928-41bf6380-5e4f-11e9-95c1-5727de1d4326.jpg)

![photo_2019-04-14_00-43-29 (2)](https://user-images.githubusercontent.com/79330/56089930-4552ea80-5e4f-11e9-8ac3-8dbdf466dc5a.jpg)

![photo_2019-04-14_00-43-29 (1)](https://user-images.githubusercontent.com/79330/56089931-47b54480-5e4f-11e9-9bdf-5183bf6a9ec6.jpg)

## License

If you distribute a copy or make a fork of the project, you have to credit this project as source.

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program.  If not, see http://www.gnu.org/licenses/.
