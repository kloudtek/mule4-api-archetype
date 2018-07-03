# mule4-api-archetype

This is a maven archetype used to create mule 4 API projects (using APIKit)

In order to use it to create a project, you can run the following command:

```
mvn archetype:generate -DarchetypeGroupId=com.kloudtek.mule -DarchetypeArtifactId=mule4-api-archetype -DarchetypeVersion=0.9.5
```

Additionally you can specify all normal maven archetype properties like groupId and artifactId. For example to create a project with group id 'com.mycompany' and artifact id 'my-system-api', you run the following command ( the -B flag is to use non-interactive batch mode )

```
mvn archetype:generate -DarchetypeGroupId=com.kloudtek.mule -DarchetypeArtifactId=mule4-api-archetype -DarchetypeVersion=0.9.5 -DgroupId=com.mycompany -DartifactId=my-system-api -B
```

Additionally, there are various optional parameters you can set.

By default a project is create to run without a domain with it's own http listener. You can however specify a domain to be used (in which case it will not create an http listener but expect one called '`http-shared`' in the shared domain.

Specifying the domain is done using multiple properties:

* domain : the domain artifact id
* domainGroupId : the domain group id
* domainVersion : the domain version

So for example:

```
mvn archetype:generate -DarchetypeGroupId=com.kloudtek.mule -DarchetypeArtifactId=mule4-api-archetype -DarchetypeVersion=0.9.5 -DgroupId=com.mycompany -DartifactId=my-system-api -Ddomain=my-shared-domain -DdomainGroupId=com.mycompany -DdomainVersion=1.0.0 -B
```

By default it will incorporate [mule-elogging](https://github.com/kloudtek/mule-elogging) to generate structured json logs as well as plain text logs. You can override which version of mule-elogging through the `eloggingVersion` property. Or if you prefer not to use elogging then set the property `jsonLogging` to false

If you want to use anypoint API Manager, you can set the property `anypointApiId` to the API ID, in which case it will add the API Discovery configuration to the project with the corresponding id

By default it will also incorporate the [anypoint tools](https://github.com/kloudtek/anypoint-tools) maven tool which provide advanced deployment capabilities. You can override which org, env and target that will be used by default for deployment using `anypointOrg`, `anypointEnv`, `anypointTarget`. You can also override which version of anypoint tools will be used with the property `anypointToolsVersion`. If you don't want the anypoint tools maven task to be added to the pom, you can set the property `useAnypointTools` to false

The project will automatically include the munit plugin and an example test. The version of the munit library can be overriden using `munitVersion`. Also by default it will set the dynamic port to be assigned to the variable `http.port`, which can be overriden using the `munitDynamicPort` property
