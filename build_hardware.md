<table style="width:100%">
  <tr>
    <th width="100%"><h2>Table of contents (steps)</h2></th>
  </tr>
  <tr>
    <td><a href="create_aws_account.md">1. Create an AWS account</a></td>
  </tr>
  <tr>
    <td><a href="generate_ssh_keys.md">2. Generate SSH keys</a></td>
  </tr>
  <tr>
    <td><a href="create_s3_credential.md">3. Create S3 credential</a></td>
  </tr>
  <tr>
    <td><a href="request_access_f1.md">4. Request access to Amazon EC2 F1 instances</a></td>
  </tr>
  <tr>
    <td><a href="create_ami_instance.md">5. Create an AMI instance</a></td>
  </tr>
  <tr>
    <td><a href="configure_s3.md">6. Configure S3 bucket</a></td>
  </tr>
  <tr>
    <td><a href="setup_development_environment.md">7. Setup development environment</a></td>
  </tr>
  <tr>
    <td><a href="simulate_design.md">8. Simulate the design</a></td>
  </tr>
  <tr>
    <td><a href="build_hardware.md">9. Build the hardware design</a></td>
  </tr>
  <tr>
    <td><a href="generate_afi.md">10. Generate the AFI</a></td>
  </tr>
  <tr>
    <td><a href="program_fpga.md">11. Program the FPGA</a></td>
  </tr>
  <tr>
    <td><a href="compile_runtime.md">12. Compile the runtime of the design</a></td>
  </tr>
  <tr>
    <td><a href="bookkeeping_afi.md">13. Bookkeping the AFI</a></td>
  </tr>
</table>

---------------------------------------

# 9. Build the hardware design

1. [Change the instance type](change_instance_type.md) for a compute optimized instance (c4.4xlarge or c5.4xlarge)
1. Connect to the instance via ssh
1. Go to the **aws-fpga** folder `cd <the-path-of-aws-fpga-folder>`
1. Setup the hardware environment `source hdk_setup.sh`
1. Go to the hello-world example folder `cd hdk/cl/examples/cl_hello_world`
1. Export environment variable for the design `export CL_DIR=$PWD`
1. Go to the hardware scripts folder `cd build/scripts`
1. Run `./aws_build_dcp_from_cl.sh`
1. Run `tail -f last_log` to monitor progress and exit anytime by running `ctrl+c`
1. Wait until Xilinx Vivado finishes building the design and the final design (.tar) will be located at `$CL_DIR/build/checkpoints/to_aws/*.Developer_CL.tar`
1. Copy the final tar-file to the s3 bucket `aws s3 cp $CL_DIR/build/checkpoints/to_aws/*.Developer_CL.tar s3://<your-s3-bucket>`
