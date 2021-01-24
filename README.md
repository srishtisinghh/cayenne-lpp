# cayenne-lpp
Java library for Cayenne Low Power Payload (https://mydevices.com/cayenne/docs/lora/#lora-how-lorawan-works)

# Quick Start
Following Groovy code shows how to use the library:
```
@Grapes([
        @GrabResolver(name='jitpack', root='https://jitpack.io'),
        @Grab ('com.github.krishnact:cayenne-lpp:-SNAPSHOT'),
])
import org.himalay.msgs.runtime.Created;
import org.himalay.msgs.runtime.IntegerHolder;
import org.himalay.lpp.LPPDataFactory;

// Temperature 
byte[] bytes = "03 67 01 10".replaceAll('\\s+',"").decodeHex()
DataInputStream dis = new DataInputStream(new ByteArrayInputStream(bytes));
org.himalay.lpp.LPPDataFactory.LPPData data = LPPDataFactory.createMsg(dis, new IntegerHolder());
data.dump();
println data.getValue()

// Acceleration
bytes = "06 71 04 D2 FB 2E 00 00".replaceAll('\\s+',"").decodeHex()
dis = new DataInputStream(new ByteArrayInputStream(bytes));
data = LPPDataFactory.createMsg(dis, new IntegerHolder());
data.dump();
```

## Converting to gradle build
 1. Edit pom.xml file at lines 48 and 49 to change 1.6 to 1.7. This fixes the maven build problem. 
 1. Run the gradle –v command into the project's root directory. This will check if gradle is properly installed. 
 1. Run gradle init in the directory containing the (master) pom.xml
 1. Run gradle build in the directory containing build.gradle files.
 1. After a few seconds, “BUILD SUCCESSFUL” indicates that the build has completed.
