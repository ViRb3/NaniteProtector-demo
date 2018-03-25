# DEMO ONLY
```
             _ _
 ___ ___ ___|_| |_ ___
|   | .'|   | |  _| -_|
|_|_|__,|_|_|_|_| |___|

            - an eXplosive Java obfuscator,
                          written in Kotlin
```

# Features
- Constant encryption (strings, integers, booleans…)
- Constant mutation
- Advanced control flow obfuscation
- Anti-tamper, anti-debug and anti-decompilation

# Technical details

## Control flow
Nanite generates non-linear code flow, making it impossible to produce readable decompilation. This is achieved by creaing fake jumps across code blocks, where the correct flow is only determined at runtime. This way a decompiler is forced to display all code flows, resulting in a 'spaghetti' output.

## Smart analysis to prevent hard obfuscation of looping code
It is no secret that obfuscation impacts performance compared to clean, unprotected code. It is however possible to minimize this effect by applying clever optimizations. One such step is to avoid overprotecting looping code, which can cause serious performance degradation. Nanite achieves this by analyzing the code flow before applying any protection and tweaking its level dynamically.

## Constant encryption
Each constant is encrypted with a unique key, dependent on the integrity of its parent method. All constants are then encrypted again and placed in a resource, with its key dependent on the integrity of all classes in the package.

## Constant mutation where encryption is inapplicable
Control flow depends on constant encryption. Constant encryption depends on a special class created by the obfuscator, regarded as its core. This core cannot be protected by itself (or an infinite loop would occur), so constant mutation is used instead, providing another, different layer of protection.

## Anti-debug and anti-decompilation
All along the core and package methods are implemented custom checks and tricks to protect against various attack vectors and automated tools.

# Sample (double cflow pass)

## Before:
```java
public static void main(String[] args) throws InterruptedException
{
    System.out.println("Welcome to the top-secret program!");
    System.out.print("Enter access key: ");
    Scanner scanner = new Scanner(System.in);
    String input = scanner.next();

    if (!input.equals("s3cr37passw0rd")) {
        System.out.println("Wrong key!");
        return;
    }

    System.out.println("Access granted! Prepare for lift off...");
    for(int i = 10; i > 0; i--)
    {
        System.out.println(i);
        Thread.sleep(1000);
    }

    liftOff();
}
```

## After:
```java
public static void main(final String[] array) throws InterruptedException {
Label_0171_Outer:
    while (true) {
        if (Яга.媝嬑媴嫤嫀婋嫣嫑媸嬹(247, 1398991613) != 0) {
            Label_0056: {
                break Label_0056;
                do {
                    System.out.print(Яга.嬄嫧媏嫊嬚媸婘婋婥婥(208, 1308995631));
                    if (Яга.媝嬑媴嫤嫀婋嫣嫑媸嬹(111, -1707728539) != 0) {
                        break;
                    }
                    System.out.println(Яга.嬄嫧媏嫊嬚媸婘婋婥婥(139, -1266279197));
                } while (Яга.媝嬑媴嫤嫀婋嫣嫑媸嬹(174, 1213956432) != 0);
            }
            final String next = new Scanner(System.in).next();
            while (true) {
                Label_0212: {
                    break Label_0212;
                Label_0155_Outer:
                    do {
                        System.out.println(Яга.嬄嫧媏嫊嬚媸婘婋婥婥(170, -239615015));
                        if (Яга.媝嬑媴嫤嫀婋嫣嫑媸嬹(201, -1206434812) == 0) {
                            return;
                        }
                        while (true) {
                            System.out.println(Яга.嬄嫧媏嫊嬚媸婘婋婥婥(155, 1362758505));
                            if (Яга.媝嬑媴嫤嫀婋嫣嫑媸嬹(201, -1206434811) != 0) {
                                for (int i = Яга.媝嬑媴嫤嫀婋嫣嫑媸嬹(105, 1874841287); i > 0; --i) {
                                    System.out.println(i);
                                    Thread.sleep(1000L);
                                }
                                liftOff();
                                if (Яга.媝嬑媴嫤嫀婋嫣嫑媸嬹(139, -1266279184) != 0) {}
                                if (Яга.媝嬑媴嫤嫀婋嫣嫑媸嬹(62, -2106222095) != 0 && Яга.媝嬑媴嫤嫀婋嫣嫑媸嬹(113, 2143052947) != 0) {}
                                return;
                            }
                            if (!next.equals(Яга.嬄嫧媏嫊嬚媸婘婋婥婥(182, -736775119))) {
                                continue Label_0155_Outer;
                            }
                            continue Label_0171_Outer;
                        }
                    } while (Яга.媝嬑媴嫤嫀婋嫣嫑媸嬹(95, 90517652) == 0);
                }
                continue;
            }
        }
        Label_0036: {
            break Label_0036;
        }
        continue;
    }
}
```