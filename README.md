# SafeOpener CTF Challenge Walkthrough (Beginner Friendly)

## Challenge Summary

- **Goal:** Recover the lost password for a virtual safe using a Java program.
- **Submission Format:** `picoCTF{password}`

---

## Step 1: Read the Challenge and Find the Java File

You are given `SafeOpener.java`. The goal is to find out what password will "open" the safe.

---

## Step 2: View the Code

Open a terminal in the folder with `SafeOpener.java` and run:

```sh
cat SafeOpener.java
```

Or open it in any text editor (VS Code, nano, vim, etc.).

---

## Step 3: Understand the Code

Key points in the code:

- The program asks you for a password.
- It encodes your input to **Base64**.
- It checks if the encoded password matches the string:
  ```
  cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz
  ```

---

## Step 4: Decode the Target String

You need to find what original password, when Base64-encoded, gives this string.

### Option A: Use the Terminal

```sh
echo cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz | base64 -d
```

### Option B: Use Python

```python
import base64
print(base64.b64decode("cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz").decode())
```

### Option C: Use an Online Tool

Visit [https://www.base64decode.org/](https://www.base64decode.org/), paste the string, and decode it.

---

## Step 5: Get the Password

The decoded string is:

```
pl3as3_l3t_m3_1nt0_th3_saf3
```

---

## Step 6: Test the Password

Compile and run the Java program:

```sh
javac SafeOpener.java
java SafeOpener
```

When prompted, enter:

```
pl3as3_l3t_m3_1nt0_th3_saf3
```

If correct, you should see:

```
Sesame open
```

---

## Step 7: Format and Submit the Flag

The flag to submit is:

```
picoCTF{pl3as3_l3t_m3_1nt0_th3_saf3}
```

---

## Recap & CTF Tips

- **Read the code carefully.** Look for checks against hidden or encoded values.
- **Recognize encoding schemes** like Base64, hex, etc.
- **Use available tools** (command line, online, Python) to decode as needed.
- **Format your answer** exactly as the challenge requires.

---

**Congrats!** You just solved a classic beginner CTF challenge. Keep practicing and you'll get even faster!
