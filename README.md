import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

class Result {

    /*
     * Complete the 'toys' function below.
     *
     * The function is expected to return an INTEGER.
     * The function accepts INTEGER_ARRAY w as parameter.
     */

    public static int toys(List<Integer> w) {
    // Write your code here
Collections.sort(w);

int containers = 0;
int i = 0;
int n = w.size();

while (i < n) {
    containers++;
    int minWeight = w.get(i);

    while (i < n && w.get(i) <= minWeight + 4) {
        i++;
    }
}

return containers;
    }

}

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int n = Integer.parseInt(bufferedReader.readLine().trim());

        String[] wTemp = bufferedReader.readLine().replaceAll("\\s+$", "").split(" ");

        List<Integer> w = new ArrayList<>();

        for (int i = 0; i < n; i++) {
            int wItem = Integer.parseInt(wTemp[i]);
            w.add(wItem);
        }

        int result = Result.toys(w);

        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();

        bufferedReader.close();
        bufferedWriter.close();
    }
}

