DoorKeeper MD5-Checksum action for MPI archival storage organisation

Building the jar: Run the command in the checked out repo ../MPI-MD5/MPI-MD5: mvn clean install

Installation: Place the MPI-MD5-1.0-SNAPSHOT.jar in the WEB-INF/lib directory of the doorkeeper (flat) web app

Configuration: 
The MD5-Checksum action configuration needs to be placed in between the action Validate and FITS in flat-deposit.xml:

	<action name="calculate checksum" class="nl.mpi.tla.flat.deposit.action.MPIChecksum">
	   <parameter name="dir" value="{$work}/checksums"/>
	   <parameter name="checksum-config" value="{$base}/policies/checksum-config.xml"/>
	</action>

Replace FOXCreate action with following in flat-deposit.xml:

	<action class="nl.mpi.tla.flat.deposit.action.FOXCreate">
		<parameter name="owner" value="{$work}/acl/owner.xml"/>
		<parameter name="fedoraConfig" value="{$base}/policies/fedora-config.xml"/>
		<parameter name="cmd2fox" value="{$base}/policies/cmd2fox.xsl"/>
		<parameter name="jar_cmd2fox" value="{$base}/transforms/cmd2fox.xsl"/>
		<parameter name="dir" value="{$work}/fox"/>
		<parameter name="icons" value="{$env-FLAT_ICON_DIR}"/>
		<parameter name="policies" value="{$work}/acl"/>
		<parameter name="policies" value="{$base}/policies"/>
		<parameter name="fits" value="{$work}/fits"/>
		<parameter name="xsl-param-mpi-checksums-dir" value="{$work}/checksums"/>
	</action>

Next, place ../MDI-MD5/MPI-MD5/flat/deposit/checksum-config.xml file under deposit/policies directory of flat.
Next, place ../MDI-MD5/MPI-MD5/flat/deposit/cmd2fox.xsl file under deposit/policies directory of flat.

