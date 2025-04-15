#!/system/bin/sh
# 实时电池状态检测
CAPACITY=$(cat /sys/class/power_supply/battery/capacity)
TEMP=$(($(cat /sys/class/power_supply/battery/temp)/10))
VOLTAGE=$(cat /sys/class/power_supply/battery/voltage_now)
CURRENT=$(cat /sys/class/power_supply/battery/current_now)
POWER_W=$(echo "scale=2; ($VOLTAGE * $CURRENT)/1000000000" | bc)
echo "电量: ${CAPACITY}% | 温度: ${TEMP}°C"
echo "电压: $((VOLTAGE/1000))mV | 功率: ${POWER_W}W"