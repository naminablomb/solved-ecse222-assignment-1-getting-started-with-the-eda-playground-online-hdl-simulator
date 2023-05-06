Download Link: https://assignmentchef.com/product/solved-ecse222-assignment-1-getting-started-with-the-eda-playground-online-hdl-simulator
<br>
In this assignment you will be required to write simple logic functions in VHDL by following a step-by-step tutorial.

<h1>4          Getting Familiar with EDA Playground</h1>

In this course you will be using the EDA Playground HDL simulator: EDA Playground supports immediate handson exposure to simulating SystemVerilog, Verilog, VHDL, C++/SystemC, and other programming languages. All you need is a web browser. The goal is to accelerate learning of design/testbench development with easier code sharing and simpler access to EDA tools and libraries.

To begin, go to the EDA Playground <a href="https://www.edaplayground.com/">website</a> and wait until the following window appears:

To access all available tools and simulators, sign up (or log in) by clicking the log in icon on the top right corner.

<h1>5        Creating a New Project</h1>

Under Language &amp; Libraries select VHDL for “<em>Testbench + Design</em>”:

You will now see two windows named testbench.vhd and design.vhd. The design.vhd window is used to describe logic circuits with VHDL and the testbench.vhd is used to perform simulations. Type the following VHDL code in the design.vhd window. This simple VHDL code describes a single logic OR gate.

Type the following VHDL code in the testbench.vhd window. The testbench is used to test all possible binary values (“0” and “1”) for the inputs <em>a </em>and <em>b</em>.

To perform (run) the simulation, type <em>testbench </em>in the box located under the Top entity. Now, select <em>Mentor Questa 2020.1 </em>under Tools &amp; Simulators and check the Open EPWave after run box.

Save your progress and Run your simulation.

The following window will pop up (EPWave). If not, make sure that your browser does not block pop ups for the EDA Playground website. The result of your simulation in the form of a waveform is plotted in this window. You can use Get Signals to add or remove signals from your waveform.

<h1>6       Synthesize your Circuit</h1>

In order to synthesize your work, you need to add a new file to your project. Create a new file by clicking on the plus (+) icon next to your testbench.vhd file and name it run.do. Then, add the following lines to the run.do file:

setup_design -manufacturer Xilinx -family Artix-7 -part 7<em>A</em>100<em>TCSG</em>324 foreach arg $::argv add_input_file $arg compile synthesize

auto_write precision.v report_output_file_list report_area report_timing exec cat precision.v

Now, select <em>Mentor Precision 2019.2 </em>under Tools &amp; Simulators and Run EDA Playground. The resulting parameters of the synthesized circuit, will be shown in the Log window:

Note that for this Lab you only need the results of Device Utilization.

Students are encouraged to visit the EDA Playground <a href="https://www.edaplayground.com/playgrounds?searchString=&amp;language=VHDL&amp;simulator=&amp;methodologies=&amp;_libraries=on&amp;_svx=on&amp;_easierUVM=on&amp;curated=true&amp;_curated=on">VHDL Examples</a> page to practice additional examples and improve their VHDL skills.

<h1>7          VHDL Implementation of a 2-to-1 MUX</h1>

A multiplexer is a circuit that selects between several inputs and forwards the selected input to a single output. In general, a 2<em><sup>n</sup></em>-to-1 MUX has 2<em><sup>n </sup></em>inputs with <em>n </em>selectors. A schematic diagram of a 2-to-1 multiplexer is shown below.

According to this schematic, the 2-to-1 multiplexer sends the input signal <em>A </em>to the output when the selector signal <em>S </em>is equal to ’0’, alternatively, the input signal <em>B </em>is sent to the output. In this lab, you will implement a 2-to-1 multiplexer in VHDL using structural and behavioral styles. In the structural modeling of the 2-to-1 multiplexer in VHDL, the multiplexer is implemented using AND, OR, and/or NOT gates only. More specifically, the structural description of the multiplexer literally realizes its Boolean function. Describe the Boolean function of the 2-to-1 MUX in VHDL using AND, OR, and/or NOT gates only. Use the following entity declaration for your VHDL description of the 2-to-1 multiplexer:

<table width="673">

 <tbody>

  <tr>

   <td width="673">library              IEEE;use IEEE.STD_LOGIC_1164.ALL; use IEEE.NUMERIC_STD.ALL;entity MUX_structural i sPort (A                                  : in              std_logic ;B                               : in              std_logic ;S                               : in              std_logic ;Y                               : out           std_logic );end MUX_structural;</td>

  </tr>

 </tbody>

</table>

Side note: You can create/add .vhd files to your project by clicking on the plus (+) icon next to your design.vhd file. Leave the design.vhd file empty as you will not use it in this assignment. Name your .vhd files the same as the entity name. Do not forget to include the file extension “.vhd” when naming your .vhd files.

Once completed, you will describe the architecture of the 2-to-1 multiplexer using the behavioral style. In the behavioral description, you desrcribe the behavior of your target circuit and the synthesis tool generates a gatelevel layout of your design. Use (only) a single VHDL select assignment and the entity declaration below to implement a behavioral description of the 2-to-1 multiplexer.

<table width="673">

 <tbody>

  <tr>

   <td width="673">library              IEEE;use IEEE.STD_LOGIC_1164.ALL; use IEEE.NUMERIC_STD.ALL;entity MUX_behavioral i sPort (A                                  : in              std_logic ;B                               : in              std_logic ;S                               : in              std_logic ;Y                               : out           std_logic );end MUX_behavioral;</td>

  </tr>

 </tbody>

</table>

Once both behavioral and structural styles of the 2-to-1 multiplexer are described in VHDL, you are required to test your circuits. Write a testbench code and perform an exhaustive test for both VHDL descriptions of the 2-to-1 multiplexer. An exhaustive test is a test that simulates the circuit for all possible input patterns.

<h1>8           VHDL Implementation of a 4-bit circular barrel shifter</h1>

In this part of the lab, you will design a circuit that implements an 4-bit circular barrel shifter. The circular barrel shifter is a circuit that can shift its input by a given number of bits using combinational logic. The 4-bit circular barrel shifter is usually implemented by stacking two layers of 2-to-1 multiplexers as shown below. All four multiplexers in the leftmost layer use sel[1] as the selector signal. Similarly, all four multiplexers in the rightmost layer use sel[0] as the selector signal. Make sure that you familiarize yourself with how the barrel shifter works by calculating its output for several input combinations by hand.

Similar to the first part of the assignment, you will implement the 4-bit barrel shifter in VHDL using both structural and behavioral styles. To obtain a structural description of the 4-bit barrel shifter, you are required to use the structural description of the 2-to-1 multiplexer. Write a structural VHDL description for the 4-bit circular barrel shifter by instantiating the structural description of the 2-to-1 multiplexer eight times. Use the following entity declaration for your structural VHDL description of the 4-bit circular barrel shifter:

<table width="673">

 <tbody>

  <tr>

   <td width="303">library                IEEE;use IEEE.STD_LOGIC_1164.ALL; use IEEE.NUMERIC_STD.ALL;entity barrel_shifter_structural i sPort (X                                   : in                       std_logic_vector</td>

   <td width="370">(3 downto 0);</td>

  </tr>

  <tr>

   <td width="303">                        sel                           : in                       std_logic_vector</td>

   <td width="370">(1 downto 0);</td>

  </tr>

  <tr>

   <td width="303">Y : out std_logic_vector end barrel_shifter_structural;</td>

   <td width="370">(3 downto 0));</td>

  </tr>

 </tbody>

</table>

Once completed, you are required to implement the 4-bit circular barrel shifter using the behavioral style. One way to obtain a behavioral description of the 4-bit circular barrel shifter is the use of VHDL select statements. Write a behavioral VHDL code for the 4-bit circular barrel shifter using (only) a single VHDL select statement. Use the following entity declaration for your behavioral VHDL description of the 4-bit circular barrel shifter:

<table width="673">

 <tbody>

  <tr>

   <td width="303">library                IEEE;use IEEE.STD_LOGIC_1164.ALL; use IEEE.NUMERIC_STD.ALL;entity barrel_shifter_behavioral i sPort (X                                   : in                       std_logic_vector</td>

   <td width="370">(3 downto 0);</td>

  </tr>

  <tr>

   <td width="303">                        sel                           : in                       std_logic_vector</td>

   <td width="370">(1 downto 0);</td>

  </tr>

  <tr>

   <td width="303">Y : out std_logic_vector end barrel_shifter_behavioral;</td>

   <td width="370">(3 downto 0));</td>

  </tr>

 </tbody>

</table>

Hint: You may want to use the VHDL concatenate operator <em>ampersand </em>(&amp;). It can be used to combine two or more signals together. Note that all input signals to the concatenation must be of the same type and the result of the concatenation needs to fit the exact width of the concatenated input signals.

Once you have your circuit described in VHDL using both structural and behavioral styles, write a testbench code and perform an exhaustive test for both VHDL descriptions of the 4-bit circular barrel shifter.

<h1>9      Deliverables</h1>

Once completed, you are required to submit a report explaining your work in detail, including answers to the questions related to this lab. You will find the questions in the next section. You must also submit all the design files (<em>i.e.</em>, your VHDL code and testbench files) along with Log content of the synthesized circuits. If you fail to submit any part of the required deliverables, you will incur grade penalaties as described in the syllabus.

<h1>10     Questions</h1>

<ol>

 <li>Explain your VHDL code.</li>

 <li>Report the number of pins and logic modules used to fit your designs on the FPGA board.</li>

</ol>

<table width="502">

 <tbody>

  <tr>

   <td width="176"> </td>

   <td colspan="2" width="154">2-to-1 MUX</td>

   <td colspan="2" width="171">4-bit circular barrel shifter</td>

  </tr>

  <tr>

   <td width="176"> </td>

   <td width="76">Structural</td>

   <td width="78">Behavioral</td>

   <td width="76">Structural</td>

   <td width="96">Behavioral</td>

  </tr>

  <tr>

   <td width="176">Logic Utilization (in LUTs)</td>

   <td width="76"> </td>

   <td width="78"> </td>

   <td width="76"> </td>

   <td width="96"> </td>

  </tr>

  <tr>

   <td width="176">Total pins</td>

   <td width="76"> </td>

   <td width="78"> </td>

   <td width="76"> </td>

   <td width="96"> </td>

  </tr>

 </tbody>

</table>

<ol start="3">

 <li>Show representative simulation plots of the 2-to-1 MUX circuits for all the possible input values (exhaustive test results). Note that you can simply include snapshots from the waveform that you obtained from EPWave. In order to fully capture all the signals from the waveform, you can adjust the display range using the magnifier icons. Make sure that all signal names and axes are properly visible.</li>

 <li>Show representative simulation plots of the 4-bit circular shift register circuits for a given input sequence,</li>

</ol>

<em>e.g.</em>, “1011” (X = “1011”), for all the possible shift amounts.