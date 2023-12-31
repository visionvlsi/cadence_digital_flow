set_db hdl_search_path {put here files path where .v files are} <br/>
set_db lib_search_path {put here files path where 'lib files are} <br/>
set myFiles [glob -directory /home/zakirhussain/Desktop/verilog/fa/src *.v] <br/>
read_hdl -sv ${myFiles} <br/>
#Specify libraries using read_libs or read_mmmc <br/>
read_lib fast.lib <br/>
elaborate fa <br/>
synthesize -to_mapped -effort medium <br/>
report gates  > /home/zakirhussain/Desktop/verilog/fa/synth/fa_cell.rep <br/>
#report timing > fa_timing.rep <br/>
report timing -unconstrained > /home/zakirhussain/Desktop/verilog/fa/synth/fa_timing.rep <br/>
report power  > /home/zakirhussain/Desktop/verilog/fa/synth/fa_power.rep <br/>
write_hdl -mapped >  /home/zakirhussain/Desktop/verilog/fa/synth/fa_synthnetlist.v <br/>
