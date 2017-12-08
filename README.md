# hibernate-tools-maven-plugin
Maven Plugin to generate JPA Entities from an existing database.

## Development status
Currently only database reverse engineering configurations (JDBCMetaDataConfiguration) with JPA Entity export (hbm2java) is supported.

## Usage
```
    <plugin>
        <groupId>com.github.stadler</groupId>
        <artifactId>hibernate-tools-maven-plugin</artifactId>
        <version>0.0.1-SNAPSHOT</version>
        <executions>
            <execution>
                <phase>generate-sources</phase>
                <goals>
                    <goal>hbm2java</goal>
                </goals>
            </execution>
        </executions>
        <configuration>
            <revengFile>${project.basedir}/src/main/hibernate/hibernate.reveng.xml</revengFile>
            <!-- Defaults:-->
            <packageName></packageName>
            <outputDirectory>${project.build.directory}/generated-sources/</outputDirectory>
            <configFile>${project.basedir}/src/main/hibernate/hibernate.cfg.xml</configFile>
            <detectManyToMany>true</detectManyToMany>
            <detectOneToOne>true</detectOneToOne>
            <detectOptimisticLock>true</detectOptimisticLock>
            <createCollectionForForeignKey>true</createCollectionForForeignKey>
            <createManyToOneForForeignKey>true</createManyToOneForForeignKey>
            <ejb3>false</ejb3>
            <jdk5>false</jdk5>
        </configuration>
        <dependencies>
            <!-- Add your DB Driver here. E.g. for H2: -->
            <dependency>
                <groupId>com.h2database</groupId>
                <artifactId>h2</artifactId>
                <version>${h2.version}</version>
            </dependency>
        </dependencies>
    </plugin>
```