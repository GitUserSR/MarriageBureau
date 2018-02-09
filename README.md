MarriageBureau(Empty Project) with below modules
    webservicerest
    webservicesoap


To create an empty multi module Maven project:
(Source-https://stackoverflow.com/questions/6328778/how-to-create-an-empty-multi-module-maven-project)

The easiest way is to use the pom-root archetype to create the top-level pom and then repeatedly use archetype:generate to create each module individually. This will automatically add the modules to the root pom (aggregator) and set the root pom as the parent pom for each module (edit: apparently some archetypes can have a hard-coded parent, but it works for maven-archetype-quickstart).

Here's the breakdown:

Create the top-level root:

mvn archetype:generate -DarchetypeGroupId=org.codehaus.mojo.archetypes -DarchetypeArtifactId=pom-root -DarchetypeVersion=RELEASE

cd into your newly created root dir.

For each module:

mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=RELEASE

Note that -DarchetypeVersion=RELEASE above will automatically use the latest version of the archetype. You may want to add -DgroupId=... to each of those commands to avoid repeating yourself.