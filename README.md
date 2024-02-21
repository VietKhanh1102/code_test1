# code_test1
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class VietnameseCharacterCounter {

    public static void main(String[] args) {
        String inputStr = "hfdawhwhcoomdd";
        int count = countVietnameseCharacters(inputStr);
        System.out.println("Input: " + inputStr);
        System.out.println("Output: " + count);
    }

    public static int countVietnameseCharacters(String inputStr) {
        // Chuyển đổi chuỗi thành chữ thường
        inputStr = inputStr.toLowerCase();

        // Thay thế các ký tự theo quy luật
        inputStr = inputStr.replace("aw", "ă")
                .replace("aa", "â")
                .replace("dd", "đ")
                .replace("ee", "ê")
                .replace("oo", "ô")
                .replace("ow", "ơ")
                .replace("w", "ư");

        // Sử dụng regex để tìm các ký tự tiếng Việt
        Pattern pattern = Pattern.compile("[ăâđêôơư]");
        Matcher matcher = pattern.matcher(inputStr);

        int count = 0;
        while (matcher.find()) {
            count++;
        }

        return count;
    }
}
