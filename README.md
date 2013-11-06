3124_Lesson1031
===============
package class3100;

import java.io.BufferedReader;
import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStreamReader;


class phone{
	int n = 20;
	int[] num = new int[n];
	String[] company = new String[n];
	String[] plan = new String[n];
	int[] kihon = new int[n];
	int[] tada = new int[n];
	double[] tuuwa = new double[n];
	double[] seikyu = new double[n];
	int time = 0;
	
	void show(int i){
		System.out.println(
				num[i] + " " +
				company[i] + " " +
				plan[i] + " " +
				kihon[i] + "円 " +
				tada[i] + "円 " +
				tuuwa[i] + "円 " +
				seikyu[i] + "円 "
				);
	}
	void calc(int i){
		//seikyu[i] = kihon[i] + tuuwa[i] * time;
		if(tuuwa[i] * time < tada[i])
			seikyu[i] = kihon[i];
		else
			seikyu[i] = kihon[i] + tuuwa[i] * time - tada[i];
	}
}
public class Lesson1031 {

	public static void main(String[] args) throws IOException {
		phone phone1;
		phone1 = new phone();
		
		File inputFile = new File("z:/database phone.txt");
		FileInputStream fis = new FileInputStream(inputFile);
		InputStreamReader isr = new InputStreamReader(fis);
		BufferedReader br = new BufferedReader(isr);
		String line = br.readLine();
		int i = 0;
		System.out.println("通話時間（分）を入力してください。");
		
		BufferedReader br1 = new BufferedReader(new InputStreamReader(System.in));
		String str = br1.readLine();
		phone1.time = Integer.parseInt(str);
			
		System.out.println("通話時間が" + phone1.time + "分の時のプランごとの料金は、");
		
		for(;;){
			line = br.readLine();
			if(line == null)
				break;
	
			String[] array;
			array = line.split("\t+");
		
			phone1.num[i] = i;
			phone1.company[i] = array[0];
			phone1.plan[i] = array[1];
			phone1.kihon[i] = Integer.parseInt(array[2]);
			phone1.tada[i] = Integer.parseInt(array[3]);
			phone1.tuuwa[i] = Double.parseDouble(array[4]);
			phone1.calc(i);
			phone1.show(i);
			i++;
		}
	
	br.close();
		
}}
