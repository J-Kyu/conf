# Install

1. ``pip3``를 통하여 appdaemon package를 설치한다.

   ```shell
   sudo pip3 install appdaemon
   ```

   * ``pip3``로 설치하는 경우, home assistant 폴더 안에 직접 appdaemon에 관한 폴더들을 생성해야 한다.

2. ``.homeassistant`` 밑에 ``conf``를 시작으로 아래와 같은 tree folder를 만든다

   ```bash
   └── .homeassistant
       ├── conf
       .	├── appdaemon.yaml
   	.   ├── custom_css
       .	├── apps
       .   .	└── app.py
       .	├── dashboards
       .   .	└── main.dash
       .	└── compiled
   	    	├── css
   	    	├── html
   	    	└── javascript
   ```

3. Appdaemon.yaml 생성

   * Appdeamon에 관한 기본적인 configuration이다

   ```yaml
   appdaemon:
     latitude: 52.379189
     longitude: 4.899431
     elevation: 2
     time_zone: Europe/Amsterdam
     plugins:
       HASS:
           type: hass
           ha_url: http://192.168.137.110:8123
           token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiI3OWZhZThkOGFmY2Q0YjZiYjQ0NzE3M2YzZWUyMzU5ZSIsImlhdCI6MTYwNjAxNzM0OSwiZXhwIjoxOTIxMzc3MzQ5fQ.4rcPn4brC0APGfZhmJyaPNaSAltErRHXVX1anUuJzL0  
   
   http:
     url: http://192.168.137.110:5050
   admin:
   api:
   hadashboard:
           dash_url: /home/homeassistant/.homeassistant/conf/dashboards
   ```

   * Token은 ``HASS.io``의 계정으로 들어가면 token을 생성할 수 있다.
     * token의 이름을 appdaemon으로 설정하고 생성된 token을 appdaemon에 추가하면 된다.

4. main.dash 생성

   * Appdaemon을 통해서 만들어질 HADashboard의 구성 configuration파일이다

   ```yaml
   #
   # Main arguments, all optional
   #
   title: Control Panel
   widget_dimensions: [1, 1]
   widget_size: [120, 120]
   widget_margins: [0, 0]
   columns: 1024
   
   global_parameters:
       use_comma: 0
       precision: 1
       use_hass_icon: 1
   
   layout:
     - sensor.led(120x120)
   ```

   

5. 실행

   ```bash
   appdaemon -c /PATH/TO/.homeassitant/conf
   ```

   * appdaemon이 위치한 path로 appdaemon을 실행하면된다.