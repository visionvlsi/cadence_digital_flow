<br/>set_attribute init_lib_search_path {/home/cad/FOUNDRY/digital/180nm/dig/lib}
<br/>set_attribute init_hdl_search_path {/home/zakirhussain/Desktop/verilog/fa/src}
<br/>set myFiles [glob -directory /home/zakirhussain/Desktop/verilog/fa/src *.v]
<br/>read_hdl -sv ${myFiles}
<br/>set_attribute library fast.lib
<br/>elaborate
<br/>#Name of the Top Module
<br/>#read_sdc /home/guests/phd/shir_16/libraries/IIR_LPF_direct1.sdc
<br/>#set_attribute syn_generic_effort medium
<br/>#set_attribute syn_map_effort medium
<br/>#set_attribute syn_opt_effort medium
<br/>#syn_generic
<br/>#syn_map
<br/>#syn_opt
<br/>#set_attr tns_opto true
<br/>#set_attr boundary_opto 1
<br/>#set_attribute hdl_preserve_unused_register true
<br/>#set_attribute delete_unloaded_seqs false
<br/>#set_attribute optimize_constant_0_flops false
<br/>#set_attribute optimize_constant_1_flops false
<br/>#set_attribute prune_unsued_logic false
<br/>synthesize -to_mapped -effort medium
<br/>write_hdl > fa_netlist.v
<br/>write_sdf > fa_sdf.sdf
<br/>#write_sdf -timescale ns -nonegchecks -recrem split -edges check_edge > delays.sdf
<br/>write_sdc > fa_sdc.sdc
<br/>#report_units
<br/>#report_units > design_units
<br/>#report_gates
<br/>report_gates > fa_design_gates.rpt
<br/>#report_power
<br/>report_power > fa_design_power.rpt
<br/>#report_timing
<br/>report_timing > fa_design_timing.rpt
<br/>#report_qor
<br/>report_qor > fa_design_qor.rpt
<br/>check_design
<br/>gui_show
