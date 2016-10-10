# 파일 입출력 과제

import java.io.BufferedReader;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.FileReader;
import java.util.Scanner;

public class Ex02_01 {
	public static void main(String[] args) throws Exception {
		FileInputStream fis = new FileInputStream("C:/Users/kimhyuk/Desktop/number.txt"); // 파일 읽기
																							
		FileReader fReader = new FileReader("C:/Users/kimhyuk/Desktop/hong.txt"); // 파일 읽기
																				
		BufferedReader bReader = new BufferedReader(fReader);
		String str = ""; // 엔터와 exit를 구분하기위해 지정한 문자열 변수
		String str2 = "";// 엔터가 입력 되었을때 System.out.print사용하여 읽어들인 문자열 한행을 보여주기위해
							// 지정한 변수

		int line_num = 0;
		Scanner sc = new Scanner(System.in);

		// line 번호 파일에서 읽고 해당라인까지 이동
		//line_num = Integer.parseInt((char)fis.read());
		char number = (char)fis.read();
		line_num = Integer.parseInt(String.valueOf(number));
		for (int i = 0; i < line_num; i++) {
			bReader.readLine();
		}

		while (true) {
			str = sc.nextLine(); // 입력

			if (str.equals("")) { //
				str2 = bReader.readLine();
				System.out.println(str2);
				line_num++;
			}

			else if (str.equals("exit")) {
				break;
			}
		}

		// 종료 후 파일 저장

		FileOutputStream fos = new FileOutputStream("C:/Users/kimhyuk/Desktop/number.txt"); 
		fos.write(String.valueOf(line_num).getBytes());
		fis.close();
		fos.close();
		bReader.close();
		fReader.close();

		return;
	}
}