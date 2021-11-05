# Yosys Example

* 來源 -- http://www.clifford.at/yosys/screenshots.html

## run

進 yosys 執行 script build.ys 指令後，會分階段產生四個檔案。

1. [counter1_synth_high.v](./counter1_synth_high.v)
    * 高階合成結果
2. [counter2_synth_low.v](./counter2_synth_low.v)
    * 低階合成結果
3. [counter3_map_dff.v](./counter3_map_dff.v)
    * 映射完 DFF 的結果
4. [counter4_map_logic.v](./counter4_map_logic.v)
    * 映射完 邏輯閘元件庫 的結果

以下為執行過程

```
$ yosys

 /----------------------------------------------------------------------------\
 |                                                                            |    
 |  yosys -- Yosys Open SYnthesis Suite                                       |    
 |                                                                            |    
 |  Copyright (C) 2012 - 2019  Clifford Wolf <clifford@clifford.at>           |    
 |                                                                            |    
 |  Permission to use, copy, modify, and/or distribute this software for any  |    
 |  purpose with or without fee is hereby granted, provided that the above    |    
 |  copyright notice and this permission notice appear in all copies.         |    
 |                                                                            |    
 |  THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES  |    
 |  WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF          |    
 |  MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR   |    
 |  ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES    |    
 |  WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN     |    
 |  ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF   |    
 |  OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.            |    
 |                                                                            |    
 \----------------------------------------------------------------------------/    

 Yosys 0.9 (git sha1 1979e0b1, i686-w64-mingw32.static-g++ 5.5.0 -Os)


yosys> script build.ys

-- Executing script file `build.ys' --

1. Executing Verilog-2005 frontend: counter.v
Parsing Verilog input from `counter.v' to AST representation.
Generating RTLIL representation for module `\counter'.
Successfully finished Verilog frontend.

2. Executing HIERARCHY pass (managing design hierarchy).

3. Executing PROC pass (convert processes to netlists).

3.1. Executing PROC_CLEAN pass (remove empty switches from decision trees).        
Cleaned up 0 empty switches.

3.2. Executing PROC_RMDEAD pass (remove dead branches from decision trees).        
Marked 1 switch rules as full_case in process $proc$counter.v:6$1 in module counter.
Removed a total of 0 dead cases.

3.3. Executing PROC_INIT pass (extract init attributes).

3.4. Executing PROC_ARST pass (detect async resets in processes).

3.5. Executing PROC_MUX pass (convert decision trees to multiplexers).
Creating decoders for process `\counter.$proc$counter.v:6$1'.
     1/1: $0\count[3:0]

3.6. Executing PROC_DLATCH pass (convert process syncs to latches).

3.7. Executing PROC_DFF pass (convert process syncs to FFs).
Creating register for signal `\counter.\count' using process `\counter.$proc$counter.v:6$1'.
  created $dff cell `$procdff$8' with positive edge clock.

3.8. Executing PROC_CLEAN pass (remove empty switches from decision trees).        
Found and cleaned up 2 empty switches in `\counter.$proc$counter.v:6$1'.
Removing empty process `counter.$proc$counter.v:6$1'.
Cleaned up 2 empty switches.

4. Executing OPT pass (performing simple optimizations).

4.1. Executing OPT_EXPR pass (perform const folding).
Optimizing module counter.

4.2. Executing OPT_MERGE pass (detect identical cells).
Finding identical cells in module `\counter'.
Removed a total of 0 cells.

4.3. Executing OPT_MUXTREE pass (detect dead branches in mux trees).
Running muxtree optimizer on module \counter..
  Creating internal representation of mux trees.
  Evaluating internal representation of mux trees.
  Analyzing evaluation results.
Removed 0 multiplexer ports.
<suppressed ~1 debug messages>

4.4. Executing OPT_REDUCE pass (consolidate $*mux and $reduce_* inputs).
  Optimizing cells in module \counter.
Performed a total of 0 changes.

4.5. Executing OPT_MERGE pass (detect identical cells).
Finding identical cells in module `\counter'.
Removed a total of 0 cells.

4.6. Executing OPT_RMDFF pass (remove dff with constant values).

4.7. Executing OPT_CLEAN pass (remove unused cells and wires).
Finding unused cells or wires in module \counter..
Removed 0 unused cells and 3 unused wires.
<suppressed ~1 debug messages>

4.8. Executing OPT_EXPR pass (perform const folding).
Optimizing module counter.

4.9. Finished OPT passes. (There is nothing left to do.)

5. Executing FSM pass (extract and optimize FSM).

5.1. Executing FSM_DETECT pass (finding FSMs in design).

5.2. Executing FSM_EXTRACT pass (extracting FSM from design).

5.3. Executing FSM_OPT pass (simple optimizations of FSMs).

5.4. Executing OPT_CLEAN pass (remove unused cells and wires).
Finding unused cells or wires in module \counter..

5.5. Executing FSM_OPT pass (simple optimizations of FSMs).

5.6. Executing FSM_RECODE pass (re-assigning FSM state encoding).

5.7. Executing FSM_INFO pass (dumping all available information on FSM cells).     

5.8. Executing FSM_MAP pass (mapping FSMs to basic logic).

6. Executing OPT pass (performing simple optimizations).

6.1. Executing OPT_EXPR pass (perform const folding).
Optimizing module counter.

6.2. Executing OPT_MERGE pass (detect identical cells).
Finding identical cells in module `\counter'.
Removed a total of 0 cells.

6.3. Executing OPT_MUXTREE pass (detect dead branches in mux trees).
Running muxtree optimizer on module \counter..
  Creating internal representation of mux trees.
  Evaluating internal representation of mux trees.
  Analyzing evaluation results.
Removed 0 multiplexer ports.
<suppressed ~1 debug messages>

6.4. Executing OPT_REDUCE pass (consolidate $*mux and $reduce_* inputs).
  Optimizing cells in module \counter.
Performed a total of 0 changes.

6.5. Executing OPT_MERGE pass (detect identical cells).
Finding identical cells in module `\counter'.
Removed a total of 0 cells.

6.6. Executing OPT_RMDFF pass (remove dff with constant values).

6.7. Executing OPT_CLEAN pass (remove unused cells and wires).
Finding unused cells or wires in module \counter..

6.8. Executing OPT_EXPR pass (perform const folding).
Optimizing module counter.

6.9. Finished OPT passes. (There is nothing left to do.)

7. Executing MEMORY pass.

7.1. Executing MEMORY_DFF pass (merging $dff cells to $memrd and $memwr).

7.2. Executing OPT_CLEAN pass (remove unused cells and wires).
Finding unused cells or wires in module \counter..

7.3. Executing MEMORY_SHARE pass (consolidating $memrd/$memwr cells).

7.4. Executing OPT_CLEAN pass (remove unused cells and wires).
Finding unused cells or wires in module \counter..

7.5. Executing MEMORY_COLLECT pass (generating $mem cells).

7.6. Executing MEMORY_MAP pass (converting $mem cells to logic and flip-flops).    

8. Executing OPT pass (performing simple optimizations).

8.1. Executing OPT_EXPR pass (perform const folding).
Optimizing module counter.

8.2. Executing OPT_MERGE pass (detect identical cells).
Finding identical cells in module `\counter'.
Removed a total of 0 cells.

8.3. Executing OPT_MUXTREE pass (detect dead branches in mux trees).
Running muxtree optimizer on module \counter..
  Creating internal representation of mux trees.
  Evaluating internal representation of mux trees.
  Analyzing evaluation results.
Removed 0 multiplexer ports.
<suppressed ~1 debug messages>

8.4. Executing OPT_REDUCE pass (consolidate $*mux and $reduce_* inputs).
  Optimizing cells in module \counter.
Performed a total of 0 changes.

8.5. Executing OPT_MERGE pass (detect identical cells).
Finding identical cells in module `\counter'.
Removed a total of 0 cells.

8.6. Executing OPT_RMDFF pass (remove dff with constant values).

8.7. Executing OPT_CLEAN pass (remove unused cells and wires).
Finding unused cells or wires in module \counter..

8.8. Executing OPT_EXPR pass (perform const folding).
Optimizing module counter.

8.9. Finished OPT passes. (There is nothing left to do.)

9. Executing Verilog backend.
Dumping module `\counter'.

10. Executing TECHMAP pass (map to technology primitives).

10.1. Executing Verilog-2005 frontend: <techmap.v>
Parsing Verilog input from `<techmap.v>' to AST representation.
Generating RTLIL representation for module `\_90_simplemap_bool_ops'.
Generating RTLIL representation for module `\_90_simplemap_reduce_ops'.
Generating RTLIL representation for module `\_90_simplemap_logic_ops'.
Generating RTLIL representation for module `\_90_simplemap_compare_ops'.
Generating RTLIL representation for module `\_90_simplemap_various'.
Generating RTLIL representation for module `\_90_simplemap_registers'.
Generating RTLIL representation for module `\_90_shift_ops_shr_shl_sshl_sshr'.     
Generating RTLIL representation for module `\_90_shift_shiftx'.
Generating RTLIL representation for module `\_90_fa'.
Generating RTLIL representation for module `\_90_lcu'.
Generating RTLIL representation for module `\_90_alu'.
Generating RTLIL representation for module `\_90_macc'.
Generating RTLIL representation for module `\_90_alumacc'.
Generating RTLIL representation for module `\$__div_mod_u'.
Generating RTLIL representation for module `\$__div_mod'.
Generating RTLIL representation for module `\_90_div'.
Generating RTLIL representation for module `\_90_mod'.
Generating RTLIL representation for module `\_90_pow'.
Generating RTLIL representation for module `\_90_pmux'.
Generating RTLIL representation for module `\_90_lut'.
Successfully finished Verilog frontend.

10.2. Continuing TECHMAP pass.
Running "alumacc" on wrapper $extern:wrap:$add:A_SIGNED=0:A_WIDTH=4:B_SIGNED=0:B_WIDTH=4:Y_WIDTH=4:394426c56d1a028ba8fdd5469b163e04011def47.
Using template $extern:wrap:$add:A_SIGNED=0:A_WIDTH=4:B_SIGNED=0:B_WIDTH=4:Y_WIDTH=4:394426c56d1a028ba8fdd5469b163e04011def47 for cells of type $extern:wrap:$add:A_SIGNED=0:A_WIDTH=4:B_SIGNED=0:B_WIDTH=4:Y_WIDTH=4:394426c56d1a028ba8fdd5469b163e04011def47.
Using extmapper simplemap for cells of type $mux.
Using extmapper simplemap for cells of type $dff.
Using template $paramod\_90_alu\A_SIGNED=0\B_SIGNED=0\A_WIDTH=4\B_WIDTH=4\Y_WIDTH=4 for cells of type $alu.
Using extmapper simplemap for cells of type $and.
Using extmapper simplemap for cells of type $xor.
Using template $paramod\_90_lcu\WIDTH=4 for cells of type $lcu.
Using extmapper simplemap for cells of type $not.
Using extmapper simplemap for cells of type $pos.
Using extmapper simplemap for cells of type $or.
No more expansions possible.
<suppressed ~151 debug messages>

11. Executing OPT pass (performing simple optimizations).

11.1. Executing OPT_EXPR pass (perform const folding).
Optimizing module counter.
<suppressed ~24 debug messages>

11.2. Executing OPT_MERGE pass (detect identical cells).
Finding identical cells in module `\counter'.
Removed a total of 0 cells.

11.3. Executing OPT_MUXTREE pass (detect dead branches in mux trees).
Running muxtree optimizer on module \counter..
  Creating internal representation of mux trees.
  No muxes found in this module.
Removed 0 multiplexer ports.

11.4. Executing OPT_REDUCE pass (consolidate $*mux and $reduce_* inputs).
  Optimizing cells in module \counter.
Performed a total of 0 changes.

11.5. Executing OPT_MERGE pass (detect identical cells).
Finding identical cells in module `\counter'.
Removed a total of 0 cells.

11.6. Executing OPT_RMDFF pass (remove dff with constant values).

11.7. Executing OPT_CLEAN pass (remove unused cells and wires).
Finding unused cells or wires in module \counter..
Removed 2 unused cells and 36 unused wires.
<suppressed ~3 debug messages>

11.8. Executing OPT_EXPR pass (perform const folding).
Optimizing module counter.

11.9. Rerunning OPT passes. (Maybe there is more to do..)

11.10. Executing OPT_MUXTREE pass (detect dead branches in mux trees).
Running muxtree optimizer on module \counter..
  Creating internal representation of mux trees.
  No muxes found in this module.
Removed 0 multiplexer ports.

11.11. Executing OPT_REDUCE pass (consolidate $*mux and $reduce_* inputs).
  Optimizing cells in module \counter.
Performed a total of 0 changes.

11.12. Executing OPT_MERGE pass (detect identical cells).
Finding identical cells in module `\counter'.
Removed a total of 0 cells.

11.13. Executing OPT_RMDFF pass (remove dff with constant values).

11.14. Executing OPT_CLEAN pass (remove unused cells and wires).
Finding unused cells or wires in module \counter..

11.15. Executing OPT_EXPR pass (perform const folding).
Optimizing module counter.

11.16. Finished OPT passes. (There is nothing left to do.)

12. Executing Verilog backend.
Dumping module `\counter'.

13. Executing DFFLIBMAP pass (mapping DFF cells to sequential cells from liberty file).
  cell DFF (noninv, pins=3, area=18.00) is a direct match for cell type $_DFF_P_.  
  create mapping for $_DFF_N_ from mapping for $_DFF_P_.
  final dff cell mappings:
    DFF _DFF_N_ (.C(~C), .D( D), .Q( Q));
    DFF _DFF_P_ (.C( C), .D( D), .Q( Q));
    unmapped dff cell: $_DFF_NN0_
    unmapped dff cell: $_DFF_NN1_
    unmapped dff cell: $_DFF_NP0_
    unmapped dff cell: $_DFF_NP1_
    unmapped dff cell: $_DFF_PN0_
    unmapped dff cell: $_DFF_PN1_
    unmapped dff cell: $_DFF_PP0_
    unmapped dff cell: $_DFF_PP1_
    unmapped dff cell: $_DFFSR_NNN_
    unmapped dff cell: $_DFFSR_NNP_
    unmapped dff cell: $_DFFSR_NPN_
    unmapped dff cell: $_DFFSR_NPP_
    unmapped dff cell: $_DFFSR_PNN_
    unmapped dff cell: $_DFFSR_PNP_
    unmapped dff cell: $_DFFSR_PPN_
    unmapped dff cell: $_DFFSR_PPP_
Mapping DFF cells in module `\counter':
  mapped 4 $_DFF_P_ cells to \DFF cells.

14. Executing Verilog backend.
Dumping module `\counter'.

15. Executing ABC pass (technology mapping using ABC).

15.1. Extracting gate netlist of module `\counter' to `<abc-temp-dir>/input.blif'..
Extracted 14 gates and 22 wires to a netlist network with 6 inputs and 4 outputs.

15.1.1. Executing ABC.
Running ABC command: <yosys-exe-dir>/yosys-abc -s -f <abc-temp-dir>/abc.script 2>&1
ABC: ABC command line: "source <abc-temp-dir>/abc.script".
ABC: 
ABC: + read_blif <abc-temp-dir>/input.blif
ABC: + read_lib -w C:\ccc\course\co\eda\yosys\example1/cmos_cells.lib
ABC: Parsing finished successfully.  Parsing time =     0.00 sec
ABC: Warning: Templates are not defined.
ABC: Libery parser cannot read "time_unit".  Assuming   time_unit : "1ns".
ABC: Libery parser cannot read "capacitive_load_unit". Assuming   capacitive_load_unit(1, pf).
ABC: Scl_LibertyReadGenlib() skipped sequential cell "DFF".
ABC: Library "demo" from "C:\ccc\course\co\eda\yosys\example1/cmos_cells.lib" has 4 cells (1 skipped: 1 seq; 0 tri-state; 0 no func; 0 dont_use).  Time =     0.00 sec
ABC: Memory =    0.00 MB. Time =     0.00 sec
ABC: + strash
ABC: + ifraig 
ABC: + scorr 
ABC: Warning: The network is combinational (run "fraig" or "fraig_sweep").
ABC: + dc2
ABC: + dretime
ABC: + retime
ABC: + strash
ABC: + &get -n
ABC: + &dch -f
ABC: + &nf
ABC: + &put
ABC: + write_blif <abc-temp-dir>/output.blif

15.1.2. Re-integrating ABC results.
ABC RESULTS:              NAND cells:        8
ABC RESULTS:               NOR cells:        8
ABC RESULTS:               NOT cells:        5
ABC RESULTS:        internal signals:       12
ABC RESULTS:           input signals:        6
ABC RESULTS:          output signals:        4
Removing temp directory.

16. Executing Verilog backend.
Dumping module `\counter'.

yosys> exit

End of script. Logfile hash: f1b86b6d63
Yosys 0.9 (git sha1 1979e0b1, i686-w64-mingw32.static-g++ 5.5.0 -Os)
Time spent: 2% 10x opt_merge (0 sec), 2% 10x opt_expr (0 sec), ...
```