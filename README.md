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

## Converting the gradle build
-  install build
-  run gradle inits