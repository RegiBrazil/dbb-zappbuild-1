# MortgageApplication
#
# Added by Regi - July 14, 2020
# 1. Created JENKSFILE at /Mortgage
#
# 2. Update datasets.properties  at    /zAppBuild/build-conf
# --> specify correct data set names
#
# 3. Updated build.properties at /zAppBuild/build-conf
# --> # updated applicationConfRootDir=${zAppBuildDir}/samples/
# ** otherwise..
# ** appConf = /var/jenkins/workspace/dbb-zappbuild-1/dbb-zappbuild-1/samples/MortgageApplication/MortgageApplication/application-conf
# Caught: com.ibm.dbb.build.ValidationException: BGZTK0045E Could not load because the file :
#  /var/jenkins/workspace/dbb-zappbuild-1/dbb-zappbuild-1/samples/MortgageApplication/MortgageApplication/application-conf/application.properties
#  does not exist in this directory.
#
# 4. Updated build.properties at /zAppBuild/build-conf
# --> Updated dbb.RepositoryClient.url=https://10.1.1.1:11043/dbb
#
# 5. Be sure that MortgageApplication/application-conf/Cobol.properties has the option below:
# cobol_compileDebugParms=TEST
# ----> For UCD
# 6. Add deploy.groovy to zAppBuild/utilities/
# 7. Add /utilities/PackageUtilities.groovy to  zAppBuild/utilities/
# 8. Add /utilities/PackageUtilities.groovy to  zAppBuild/utilities/
# 9. Add /build-conf/build.yaml to  zAppBuild/build-conf/
#10. Replace /utilities/ImpactUtilities.groovy from geanapp to  /utilities/ImpactUtilities.groovy
#11.  Change build.groovy: Look for below
// props.buildOutDir = ((props.userBuild) ? "${props.outDir}" : "${props.outDir}/${props.applicationBuildLabel}") as String
# comment the line and replace by below..
// do not create a subfolder for user builds
	props.buildOutDir = ((props.userBuild) ? "${props.outDir}" : "${props.outDir}") as String
#
# =======================================================================
This version of the MortgageApplication sample is designed to be built by zAppBuild.

**Example showing how to build all programs in MortgageApplication**
```
$DBB_HOME/bin/groovyz build.groovy --workspace /u/build/repos/dbb-zappbuild/samples --application MortgageApplication --outDir /u/build/out --hlq BUILD.MORTAPP --fullBuild
```
See [BUILD.md](../../../BUILD.md) for additional information about building applications using zAppBuild.
