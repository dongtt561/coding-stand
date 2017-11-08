PHP Coding Convention  

1. Chuẩn đặt tên 
- Tên biến:
    Tên biến phải có ý nghĩa so với giá trị của biến mô tả, đặt theo chuẩn snake_case (các kí tự viết thường, phân cách giữa các từ bằng dấu gạch dưới)
    Tên biến không được viết tắt 
    Nếu là array thì kết thúc bằng 's'
    Ví dụ:
        user_name
        array : users_name
- Tên hàm: Tên hàm đặt theo định dạng camelCase (viết hoa chứ cái đầu tiên của mỗi từ, trừ từ đầu tiên của tên hàm)
    Ví dụ:
        public function checkChannel();
- Tên lớp (class): Tên lớp đặt theo chuẩn PascalCase (viết hoa chứ cái đầu tiên của mỗi từ)
    Ví dụ:
        class ClientUsers
        {
        
        }
- Tên hằng: Tên hằng phải được viết hoa toàn bộ và sử dụng gạch dưới ngăn cách giữa các từl;
    Ví dụ:
        PARAM_ONE = 'param_one';
        class ClientUsers
        {
            const = ACTIVE_STATUS = 1;
        }
- Tên file: Tên file phải trùng với tên class, nếu là file autoload thì tên file đặt theo chuẩn snake_case
    Ví dụ:
        ClientUsers.php //  file chứa class ClientUsers;
        constants_configure.php // file autoload

2. Chuẩn viết code
- Toán tử (=, ==, ., -, +, *, /,...)
    Hai bên của hai toán tử phải có kí tự space
    Ví dụ:
        $a = 1 + 1; // Đúng format
        $b = 1+1; // Sai format
- Khai báo hằng số, tham số của lớp
    Khai báo hằng số, tham số mới của lớp phải đi kèm theo comment với format như ví dụ dưới
    ví dụ:
        class ClassName()
        {
            /**
             * Constant description
             * @var String
             */
            const DESCRIPTION = 'description';

            /**
             * Variable description
             * @var Int
             */
            private $variable;
        }
- Cách viết hàm
    Hàm mới phải có comment theo format:
    /** 
     * Meaning of function  
     * @param <type> $var
     * @param <type> $var2
     * @return <type>
     */
    public funtion functionName()
    {
        //
    }

    Trong đó: type nằm trong các giá trị sau: String, Integer, Float, Array, Object, Boolean, Mix;

    Ví dụ :
        /** 
         * Meaning of function  
         * @param Integer $channel
         * @param String $user
         * @return Array
         */
        public function checkChannel($channel, $user)
        {
        }

        /** 
         * Meaning of function  
         * @param Integer $channel
         * @param String $user
         * @return Boolean
         */
        function checkChannel($channel, $user)
        {
        }

    Quy định khác: dấu mở khối code của hàm ({) phải được xuống dòng, trừ trường hợp function viết trong interface.
        Ví dụ:
            private function functionName() {}; // interface
            private function functionName() // class
            {

            }
- Cấu trúc rẽ nhánh và lặp:
    Khối điều kiện phải đặt trong ngoặc tròn (()) được tách với câu lệnh khác bằng kí tự space
    khối thực thi phải được đặt trong ngoặc nhọn, dấu mở khối cùng dòng với dòng đầu tiên của câu lênh, dấu kết thúc khối viết tương tự như function
    Ví dụ:
        if (1 == 1) {
            echo "Một bằng một";
        }

        while (true) {
            echo "đúng rồi";
            break;
        }

        foreach ($users as $user) {
            echo $user->id;
        }

        // Sai format:
        if() { // thiếu space sau if
        }

        if () // Dấu mở khối sau phải đặt cùng dòng với if
        {

        }

3. Quy định khác
- Dấu tab:
    Một tab bằng 4 space, dùng kí tự space ('    '), không dùng kí tự tab ('    ');
    Thụt vào 1 tab so với câu lệnh đầu của khối sau dấu mở khối thực thi ({):
        ví dụ:
            while (true) {
                echo "đúng rồi";
                break;
            }

            while (true) {
            echo "đúng rồi"; // Sai format
                break;
            }
    Không để 2 dấu space liên tiếp không có nghĩa.
    Không để 2 kí tự xuống dòng liên tiếp không có nghĩa.
- Một số quy định về code smell:
    Không được lồng nhau quá 3 khối lệnh rẽ nhánh và lặp (if / when / do-while / while / for / foreach) trong một khối thực thi;
        Ví dụ:
            if ($a =< $b) { // tầng 1
                while ($a != 0) { // tầng 2
                    for ($i = 0; $i < $b; $i++) { // tầng 3
                        if ($i == $a) { // sai format
                            // do something
                        }
                    }
                }
            }
    Không dùng quá 3 return trong một hàm.
    Không được khai báo biến khi không sử dụng.
        Ví dụ:
            foreach ($users as $key => $user) { // Biến $key không sử dụng
                $user->name = 'name';
            } 


    
