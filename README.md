# SafeOpener & SafeOpener 2 - CTF Walkthrough (Beginner Friendly)

---

## SafeOpener (Java Source Provided)

### 1. Download & View the Code

After downloading `SafeOpener.java`, open your terminal in the same folder and run:

```sh
cat SafeOpener.java
```
Or open it in a text editor.

---

### 2. Understand the Code

- The program asks for a password.
- It encodes your input with Base64.
- It checks if your encoded input matches:
  ```
  cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz
  ```

---

### 3. Decode the Target String

Use your terminal, python, or an online tool.

**Terminal:**
```sh
echo cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz | base64 -d
```

**Python:**
```python
import base64
print(base64.b64decode("cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz").decode())
```

**Online:**  
[https://www.base64decode.org/](https://www.base64decode.org/)

---

### 4. Get the Password

Decoded value:

```
pl3as3_l3t_m3_1nt0_th3_saf3
```

---

### 5. Test the Password

Compile and run the Java file:

```sh
javac SafeOpener.java
java SafeOpener
```
Enter:
```
pl3as3_l3t_m3_1nt0_th3_saf3
```
You should see:  
`Sesame open`

---

### 6. Format the Flag

```
picoCTF{pl3as3_l3t_m3_1nt0_th3_saf3}
```

---

## SafeOpener 2 (Class File Provided)

### 1. Download & View the File

After downloading `SafeOpener.class`, you might see it contains unreadable binary data if you try:

```sh
cat SafeOpener.class
```

### 2. Decompile the Class File

You need to reverse the compiled Java code. Use a Java decompiler.

#### **Option A: Online Decompiler**
- Go to [https://www.javadecompilers.com/](https://www.javadecompilers.com/)
- Upload your `SafeOpener.class` file.
- The site will show you the readable Java code.

#### **Option B: Use `javap` (for method names/strings)**
If you can't use an online tool, you can often reveal useful strings with:

```sh
strings SafeOpener.class
```

Look for anything that looks like a flag, password, or check.

---

### 3. Analyze for the Flag

In your `strings` output, you may see something like:

```
picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_198203f7}
```

or

- If you decompiled the file, look for any hardcoded strings or logic that prints or checks for a password/flag.

---

### 4. Submit the Flag

Flag from the `.class` file:
```
picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_198203f7}
```

---

## General Tips for Both Challenges

- **If you get a `.java` file:** read the code and look for checks or encodings.
- **If you get a `.class` file:** decompile it or search for strings to find flags or passwords.
- **Use online tools:** for decoding (Base64, hex) or decompiling (`.class` files).
- **Always format your answer** as required, e.g., `picoCTF{your_flag_here}`.

---

**Congratulations!**  
You just learned how to analyze both Java source and compiled class files for CTFs.
