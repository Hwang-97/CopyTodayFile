πΏCopyTodayFileπ 

![image](https://user-images.githubusercontent.com/85034286/153548713-f4021bfc-bda9-4f57-9c5a-142fc99771c2.png)


>  νμΌ νμκ΄λ¦¬ νλ‘κ·Έλ¨ <br />
>  1μΌκ° μ§νλ νλ‘μ νΈ μλλ€. <br />

<br />

# π Table Of Contents
* [π Introduction](#-introduction)
* [π Detail](#-detail)
* [π‘ Review](#-review)

<br />
<br />
<br />



# π Introduction
### 1. νλ‘μ νΈ κ°μ
* ν΄λΉ νλ‘μ νΈλ λ€νΈμν¬κ° λΆμμ  νκ±°λ μλ νκ²½μμλ νμΌμ νμ κ΄λ¦¬λ₯Ό νκΈ° μν΄ μμν νλ‘μ νΈ μλλ€.
1. λ³΅μ¬ν  νμΌμ΄ μ‘΄μ¬νλ ν΄λλ₯Ό μ ν
2. λ³΅μ¬λ  ν΄λλ₯Ό μλ ₯ν©λλ€.
3. λ³΅μ¬ν  νμΌ νμ₯μλ₯Ό μ μΌλ©΄ νλ‘κ·Έλ¨μ΄ ν΄λΉ ν΄λ λ΄λΆλ₯Ό μμ νμνλ©° μ νν νμ₯μμ νμΌμ λͺ¨λ κ²μν©λλ€.
4. λΉμΌ μμ λ νμΌμ΄ μλ€λ©΄ μ ν΄μ§ ν΄λμ λΉμΌ λ μ§ ν΄λλ₯Ό λ§λ€κ³  λ΄λΆμ νμΌμ λ³΅μ¬νλ λ°©μμΌλ‘ μ€ν λ©λλ€.
<br />

### 2. κ°λ° νκ²½
<img src="https://img.shields.io/badge/java-007396?style=for-the-badge&logo=java&logoColor=white"> 

* ν΄λΉ νλ‘μ νΈλ μμ μλ° κΈ°λ°μΌλ‘ μ΄λ£¨μ΄μ Έ μμ΅λλ€.
* Eclipseλ₯Ό νμ©νμ¬ μ μνμμ΅λλ€.
<br />

### 3. νλ‘μ νΈ λ΄μ©
![image](https://user-images.githubusercontent.com/85034286/153548111-6b4a0412-9ac4-44ee-8b0b-9a5c18688bb4.png)
![image](https://user-images.githubusercontent.com/85034286/153548720-950b221c-ac32-4df2-985a-032ba74f1f93.png)

**πκ΅¬ν λμ**

![μ€λ μμ λ νμΌ λ³΅μ¬ νλ‘μ νΈ](https://user-images.githubusercontent.com/85034286/153561670-e2888b75-4bef-4d98-8de6-cfb6597b0db1.gif)

<br />
<br />
<br />

# π Detail
### 1. μ£Όμ μ½λ
* μ§μ ν ν΄λ λ΄λΆμ λͺ¨λ  νμΌμ μ¬κ·λ‘ νμνλ λ©μλ μλλ€.
    ```java
    private static void foundFile(File file) {
		File[] dir = file.listFiles();

		for (File f : dir) {
			String extension = f.getName().substring(f.getName().lastIndexOf(".")+1);
			extension.toLowerCase();
			extension.equals(selctExtension);
			if (f.isFile()
					&& extension.equals(selctExtension)) {
				Date d = new Date(f.lastModified());
				String date2 = String.format("%tF", d);// μ°Ύμ νμΌμ λ§μ§λ§ μμ  λ μ§ νμΈνμ¬ νμ¬ λ μ§μ κ°λ€λ©΄ λ³΅μ¬
				String parent = f.getParent().substring(f.getParent().lastIndexOf("\\") + 1);
				if (date.equals(date2)) {
					file2.mkdir();
					File resultFile1 = new File(path2 + "\\" + parent);
					resultFile1.mkdirs();
					String name = f.getName();
					File resultFile2 = new File(path2 + "\\" + parent + "\\" + name);
					String txt = readFile(f);
					writFile(resultFile2, txt);
				}
			}
		}
		for (File subdir : dir) {
			if (subdir.isDirectory()) {
				foundFile(subdir);
			}
		}
	}
    ```
* μ‘°κ±΄μ λͺ¨λ λ§μ‘±ν μ νΈμΆλλ λ©μλλ‘μ¨ ν΄λ μ£Όμμ νμΌμ μ λ³΄κ° μΈμλ‘ μ λ¬ λ©λλ€. 
* μ΄ν ν΄λΉ λ©μλμμ BufferedWriter λ₯Ό μ΄μ©ν΄μ νμΌμ λ³΅μ¬ ν©λλ€.
    ```java
    private static void writFile(File resultFile, String txt) {

		try {
			BufferedWriter writer = new BufferedWriter(new FileWriter(resultFile));

			writer.write(txt);

			writer.close();

		} catch (IOException e) {

			e.printStackTrace();
		}

	}
    ```
* μ‘°κ±΄μ λͺ¨λ λ§μ‘±νλ νμΌ λ°κ²¬μ νΈμΆλλ λ©μλλ‘μ¨ ν΄λΉ νμΌμ λͺ¨λ μ½μ λ€ String ννλ‘ λ°ννλ λ©μλ μλλ€.
    ```java
    public static String readFile(File file2) {
		String txt = "";

		try {
			BufferedReader reader = new BufferedReader(new FileReader(file2));
			String line = null;
			while ((line = reader.readLine()) != null) {
				txt += line + "\r\n";
			}
		} catch (Exception e) {
			e.printStackTrace();
		}
		return txt;
	}
    ```
    
<br />
<br />
<br />

# π‘ Review
### 1. νκΈ°
* ν΄λΉ νλ‘μ νΈλ₯Ό μ§ννλ©΄μ μλ¬΄ μλνλ μ΄λ° λ§₯λ½μΌλ‘ μ§νλμ§ μμκΉ μ€μ€λ‘ λ§μ μκ°μ νκ² λμλ νλ‘μ νΈμ΄λ©° 
* νμ λ±λ‘ν κ°μ₯ λ¨Όμ  μμν νλ‘μ νΈ μλ λ§νΌ JAVAμ μμ κ°μ λΆμ΄λ£κ² λμλ κ³κΈ°μκ³ 
* μμ§λ§ μ μ°©μ΄ λ§μ΄ κ°λ νλ‘κ·Έλ¨ μλλ€.
* μ²« νλ‘μ νΈ μλ λ§νΌ UIκ΅¬μ±μ΄ μμ½κ³  , GUI λ±μ νμ©νμΌλ©΄ λμΌν μκ³ λ¦¬μ¦μΌλ‘ λμ± λ©μ§ νλ‘κ·Έλ¨μ λ§λ€ μ μμ§ μμμκΉ νλ μμ¬μμ΄ μμ΅λλ€.

<br />
<br />

### 2. κ°μ  
* GUI λ±μ νμ©ν΄μ λμ± μ€μ©μ± μλ νλ‘κ·Έλ¨μΌλ‘ μκ·Έλ μ΄λ νλ©΄ μ’μκ² κ°μ΅λλ€.

<br />
<br />
<br />
