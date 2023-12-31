#Command to invoke : genus -legacy_ui -f ../synth/synth.tcl

<br/>set synthFiles /home/zakirhussain/Desktop/verilog/fa3/synth
<br/>set_attribute init_lib_search_path {/home/cad/FOUNDRY/digital/180nm/dig/lib}
<br/>set_attribute init_hdl_search_path {/home/zakirhussain/Desktop/verilog/fa3/src}
<br/>read_hdl {fa.v ha.v orgate.v}
<br/>#set myFiles [glob -directory /home/zakirhussain/Desktop/verilog/fa/src *.v]
<br/>#read_hdl -sv ${myFiles}
<br/>set_attribute library fast.lib
<br/>elaborate
<br/>synthesize -to_mapped -effort medium
<br/>write_hdl > $synthFiles/fa_netlist.v
<br/>write_sdf > $synthFiles/fa_sdf.sdf
<br/>write_sdc > $synthFiles/fa_sdc.sdc
<br/>report_gates > $synthFiles/fa_design_gates.rpt
<br/>report_power > $synthFiles/fa_design_power.rpt
<br/>report_timing > $synthFiles/fa_design_timing.rpt
<br/>report_qor > $synthFiles/fa_design_qor.rpt
<br/>check_design
<br/>gui_show
