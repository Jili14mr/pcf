...

stage("Read Manifest Config") {
	node {
		def configVal = readYaml file: "manifest.yml"
		echo "configVal: " + configVal
		
		env.APP_NAME = configVal['applications']['name'][0]
		env.STACK = configVal['applications']['stack'][0]
		env.BUILD_PACK = configVal['applications']['buildpacks'][0][0]
	}
}

stage("Deploy") {
	node {
		sh '''
			...
			
			cf push ${APP_NAME} -b ${BUILD_PACK} -p build/libs/artifact_name.jar -s ${STACK} --no-start
			
			...		
		'''
	}
}
