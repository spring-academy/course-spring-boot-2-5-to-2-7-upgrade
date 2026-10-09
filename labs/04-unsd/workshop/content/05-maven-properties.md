As we've mentioned in the previous lesson and in this very lab, it is a best practice to manage required hard-coded dependency versions all in one place using Maven Properties. Let's do this for the `itextpdf` dependency.

1. Replace the the version with a property.

   Update `itextpdf`'s hard-coded version with a well-named property, which we'll create in the next step:

   ```xml
   <dependency>
       <groupId>com.itextpdf</groupId>
       <artifactId>itextpdf</artifactId>
       <version>${itextpdf.version}</version>
   </dependency>
   ```

   This is property that will be set at the top of the document in the `<properties>` section.

2. Create the property.

   Jump up the top of the `pom.xml` file and update the `<properties>` section, adding our new property for `itextpdf`'s version:

   ```xml
   <properties>
      <java.version>1.8</java.version>
      <itextpdf.version>5.5.13.3</itextpdf.version>
      ...
   </properties>
   ```

Done! Let's see how this impacted the project.
