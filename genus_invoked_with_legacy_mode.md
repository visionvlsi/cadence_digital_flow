set_attribute init_lib_search_path {/home/cad/FOUNDRY/digital/180nm/dig/lib}
set_attribute init_hdl_search_path {/home/zakirhussain/Desktop/verilog/fa/src}
set myFiles [glob -directory /home/zakirhussain/Desktop/verilog/fa/src *.v]
read_hdl -sv ${myFiles}
set_attribute library fast.lib
elaborate
#Name of the Top Module
#read_sdc /home/guests/phd/shir_16/libraries/IIR_LPF_direct1.sdc
#set_attribute syn_generic_effort medium
#set_attribute syn_map_effort medium
#set_attribute syn_opt_effort medium
#syn_generic
#syn_map
#syn_opt
#set_attr tns_opto true
#set_attr boundary_opto 1
#set_attribute hdl_preserve_unused_register true
#set_attribute delete_unloaded_seqs false
#set_attribute optimize_constant_0_flops false
#set_attribute optimize_constant_1_flops false
#set_attribute prune_unsued_logic false
synthesize -to_mapped -effort medium
write_hdl > fa_netlist.v
write_sdf > fa_sdf.sdf
#write_sdf -timescale ns -nonegchecks -recrem split -edges check_edge > delays.sdf
write_sdc > fa_sdc.sdc
#report_units
#report_units > design_units
#report_gates
report_gates > fa_design_gates.rpt
#report_power
report_power > fa_design_power.rpt
#report_timing
report_timing > fa_design_timing.rpt
#report_qor
report_qor > fa_design_qor.rpt
check_design
gui_show
