<!--
 * @Author        : fineemb
 * @Github        : https://github.com/fineemb
 * @Description   : 
 * @Date          : 2019-10-31 12:03:02
 * @LastEditors   : fineemb
 * @LastEditTime  : 2020-04-19 23:53:11
 -->
lovelace-remote-card
================================================

[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg)](https://github.com/custom-components/hacs)

这是一个通用的电视(机顶盒)遥控器卡片, 可以自定义设置额外的按钮

![slider-entity-row](https://raw.githubusercontent.com/fineemb/lovelace-remote-card/d6561e8724a15359ef5044478a3b2346c37ae4cb/01.gif)

## 使用

!> 注意：只支持script

增加这个卡片到你的Yaml或者UI编辑器
```yaml
type: 'custom:lovelace-remote-card'
vibrate: true
entity: binary_sensor.tian_mao_mo_he
circle:
  ok: script.yao_kong_select
  up: script.yao_kong_up
  down: script.yao_kong_down
  left: script.yao_kong_left
  right: script.yao_kong_right
left_buttons:
  - entity: script.chuang_wei_dian_shi_kai_guan
    icon: 'mdi:monitor'
  - entity: script.tian_mao_mo_he_kai_guan
    icon: 'mdi:set-top-box'
  - entity: script.yao_kong_power_on
    icon: 'mdi:power'
  - entity: script.yao_kong_back
    icon: 'mdi:keyboard-return'
  - entity: script.yao_kong_home
    icon: 'mdi:home'
  - entity: script.yao_kong_menu
    icon: 'mdi:menu'
  - entity: script.yao_kong_volume_down
    icon: 'mdi:volume-minus'
  - entity: script.yao_kong_volume_up
    icon: 'mdi:volume-plus'
```

小米电视遥控
```yaml
type: 'custom:lovelace-remote-card'
vibrate: true
entity: media_player.xiao_mi_dian_shi
circle:
  ok: 
    service: remote.send_command
    data:
      command: enter
      entity_id: remote.xiao_mi_dian_shi
  up: 
    service: remote.send_command
    data:
      command: up
      entity_id: remote.xiao_mi_dian_shi
  down: 
    service: remote.send_command
    data:
      command: down
      entity_id: remote.xiao_mi_dian_shi
  left: 
    service: remote.send_command
    data:
      command: left
      entity_id: remote.xiao_mi_dian_shi
  right: 
    service: remote.send_command
    data:
      command: right
      entity_id: remote.xiao_mi_dian_shi
left_buttons:
  - icon: 'mdi:power'
    service: remote.send_command
    data:
      command: power
      entity_id: remote.xiao_mi_dian_shi
  - icon: 'mdi:keyboard-return'
    service: remote.send_command
    data:
      command: back
      entity_id: remote.xiao_mi_dian_shi
  - icon: 'mdi:home'
    service: remote.send_command
    data:
      command: home
      entity_id: remote.xiao_mi_dian_shi
  - icon: 'mdi:menu'
    service: remote.send_command
    data:
      command: menu
      entity_id: remote.xiao_mi_dian_shi
  - icon: 'mdi:volume-minus'
    service: remote.send_command
    data:
      command: volumedown
      entity_id: remote.xiao_mi_dian_shi
  - icon: 'mdi:volume-plus'
    service: remote.send_command
    data:
      command: volumeup
      entity_id: remote.xiao_mi_dian_shi
```
## 属性

!> 注意：只支持script

- `circle`
  * `up` 上 
  * `down` 下
  * `left` 左
  * `right` 右
  * `ok` 确认
- `left_buttons` 左侧按钮支持`script` 可以添加任意数量,但是建议在6或者8个,为的是UI的和谐. 格式严格按照示例
- `vibrate` (选项)设置按钮震动反馈是否开启True/False
- `entity` (选项) 可以指定设备的追踪ID,一般是路由器追踪,判断电视是否在线
