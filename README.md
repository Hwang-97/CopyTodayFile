![image](https://user-images.githubusercontent.com/85034286/153548713-f4021bfc-bda9-4f57-9c5a-142fc99771c2.png)


>  파일 형상관리 프로그램 <br />
>  1일간 진행된 프로젝트 입니다. <br />

<br />

# 📌 Table Of Contents
* [📖 Introduction](#-introduction)
* [🔎 Detail](#-detail)
* [💡 Review](#-review)

<br />
<br />
<br />



# 📖 Introduction
### 1. 프로젝트 개요
* 해당 프로젝트는 네트워크가 불안정 하거나 없는 환경에서도 파일의 형상 관리를 하기 위해 시작한 프로젝트 입니다.
1. 복사할 파일이 존재하는 폴더를 선택
2. 복사될 폴더를 입력합니다.
3. 복사할 파일 확장자를 적으면 프로그램이 해당 폴더 내부를 완전탐색하며 선택한 확장자의 파일을 모두 검색합니다.
4. 당일 수정된 파일이 있다면 정해진 폴더에 당일 날짜 폴더를 만들고 내부에 파일을 복사하는 방식으로 실행 됩니다.
<br />

### 2. 개발 환경
<img src="https://img.shields.io/badge/java-007396?style=for-the-badge&logo=java&logoColor=white"> 

* 해당 프로젝트는 순수 자바 기반으로 이루어져 있습니다.
* Eclipse를 활용하여 제작하였습니다.
<br />

### 3. 프로젝트 내용
![image](https://user-images.githubusercontent.com/85034286/153548111-6b4a0412-9ac4-44ee-8b0b-9a5c18688bb4.png)
![image](https://user-images.githubusercontent.com/85034286/153548720-950b221c-ac32-4df2-985a-032ba74f1f93.png)

**😁구현 동작**

![오늘 수정된 파일 복사 프로젝트](https://user-images.githubusercontent.com/85034286/153561670-e2888b75-4bef-4d98-8de6-cfb6597b0db1.gif)

<br />
<br />
<br />

# 🔎 Detail
### 1. 주요 코드
* 지정한 폴더 내부의 모든 파일을 재귀로 탐색하는 메소드 입니다.
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
				String date2 = String.format("%tF", d);// 찾은 파일의 마지막 수정 날짜 확인하여 현재 날짜와 같다면 복사
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
* 조건에 모두 만족할시 호출되는 메소드로써 폴더 주소와 파일의 정보가 인자로 전달 됩니다. 
* 이후 해당 메소드에서 BufferedWriter 를 이용해서 파일을 복사 합니다.
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
* 조건에 모두 만족하는 파일 발견시 호출되는 메소드로써 해당 파일을 모두 읽은 뒤 String 형태로 반환하는 메소드 입니다.
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

# 💡 Review
### 1. 후기
* 해당 프로젝트를 진행하면서 업무 자동화도 이런 맥락으로 진행되지 않을까 스스로 많은 생각을 하게 되었던 프로젝트이며 
* 학원 등록후 가장 먼저 시작한 프로젝트 였던 만큼 JAVA에 자신감을 불어넣게 되었던 계기였고
* 작지만 애착이 많이 가는 프로그램 입니다.
* 첫 프로젝트 였던 만큼 UI구성이 아쉽고 , GUI 등을 활용했으면 동일한 알고리즘으로 더욱 멋진 프로그램을 만들 수 있지 않았을까 하는 아쉬움이 있습니다.

<br />
<br />

### 2. 개선 
* GUI 등을 활용해서 더욱 실용성 있는 프로그램으로 업그레이드 하면 좋을것 같습니다.

<br />
<br />
<br />
