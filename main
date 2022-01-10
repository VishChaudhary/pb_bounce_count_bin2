;
; pb_bounce_count_bin2.asm
;
; Created: 10/13/2021 2:34:24 PM
; Author : vish75000
; Target: AVR128DB48
; Replace with your application code

start:

                          ; I/O port configuration
ldi r16, 0xFF             ;load r16 with all 1s
out VPORTD_DIR, r16       ;Configure VPORTD as output
out VPORTD_OUT, r16       ;VPORTD output all 1s
cbi VPORTE_DIR, 0         ;setting E0 as input
ldi r16, 0x00             ;load r16 with all 0s

wait_for_1:
sbic VPORTE_IN, 0         ;wait for PE0 to be 1
rjmp wait_for_1

wait_for_0:
sbis VPORTE_IN, 0         ;wait for PE0 to be 0
rjmp wait_for_0
inc r16                   ;negative edge increment counter
com r16
out VPORTD_OUT, r16

chech_for_FF:
cpi r16, 0xFF             ;compare r16 to $FF (1111 1111)
breq FF_clear             ;branch if it equals $FF
rjmp wait_for_1

FF_clear:
andi r16, 0x00            ;clear the counter once count reaches $FF
rjmp wait_for_1
