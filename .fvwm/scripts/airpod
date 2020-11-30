#!/bin/sh
# Check whether the headphones (or speakers) are plugged in or not.
# Usage:
#   checkHeadphones > /dev/null
#   if [ $? -eq 0 ]; then
#     echo "Headphones are connected"
#   else
#     echo "Headphones are not connected"
#   fi

snd_card_num=0
node_num="0x16"
snd_card_file="/proc/asound/card${snd_card_num}/codec#0"

# Run the check
cat "${snd_card_file}" \
    | grep -A 4 'Node $node_num' \
    | grep 'Amp-Out vals:  \[0x00 0x00\]' \
    > /dev/null

exit_state=$?

if [ $exit_state -eq 0 ]; then
    state="connected"
else
    state="disconnected"
fi

echo "$state"
exit $exit_state