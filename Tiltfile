# Build
custom_build(
    # Name of the container image
    ref = 'config-service:latest',
    # Command to build the container image
    # On Windows, replace $EXPECTED_REF with %EXPECTED_REF%
    command = 'mvn spring-boot:build-image -Dmaven.test.skip=true -D"spring-boot.build-image.imageName"=%EXPECTED_REF%',
    deps = ['pom.xml', 'src']
)

# Deploy
k8s_yaml(['k8s/deployment.yml', 'k8s/service.yml'])

# Manage
k8s_resource('config-service', port_forwards=['8888'])