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

# 11. Program the FPGA

1. Change to an FPGA instance **f1.2xlarge** or **f1.16xlarge**, [follow these steps](change_instance_type.md)
1. Connect the instance via ssh
1. Go to the aws-fpga folder `cd <the-path-of-aws-fpga-folder>`
1. Setup the software environment `source sdk_setup.sh`
1. Clear the FPGA `sudo fpga-clear-local-image -S 0`
1. Program the FPGA `sudo fpga-load-local-image -S 0 -I <FPGA-image-global-ID>`
1. Get info about the FPGA `sudo fpga-describe-local-image -S 0 -H`
1. The option **-S** is related to the ID of the FPGA, this is important for instances having more than
one FPGA i.e. **f1.16xlarge**
