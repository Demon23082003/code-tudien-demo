using System;
 using System.Collections.Generic; 
using System.Linq; 
using System.Windows.Forms;

namespace UserManagementApp
 { 
public partial class UserManagementForm : Form 
{ 
private List<User> users = new List<User>(); // Danh sách lưu trữ người dùng
public UserManagementForm()
 { InitializeComponent(); } 
private void btnRegister_Click(object sender, EventArgs e) 
{
 // Đăng ký người dùng User newUser = new User 
{
Username = txtUsername.Text, Password = txtPassword.Text, FullName = txtFullName.Text, Age = Convert.ToInt32(txtAge.Text), PhoneNumber = txtPhone.Text 
};
users.Add(newUser); RefreshGrid(); 
}
private void btnLogin_Click(object sender, EventArgs e) 
{ // Đăng nhập string username = txtUsername.Text; string password = txtPassword.Text; User user = users.FirstOrDefault(u => u.Username == username && u.Password == password);
 if (user != null) { // Người dùng đăng nhập thành công
MessageBox.Show("Đăng nhập thành công!");
 } 
else 
{ 
MessageBox.Show("Đăng nhập thất bại. Vui lòng kiểm tra lại tên người dùng và mật khẩu."); 
} 
}
private void btnUpdate_Click(object sender, EventArgs e)
 { 
// Sửa thông tin người dùng
 // Xác định người dùng cần sửa thông tin dựa vào tên đăng nhập
 string username = txtUsername.Text;

User userToUpdate = users.FirstOrDefault(u => u.Username == username); 
if (userToUpdate != null) 
{
userToUpdate.Password = txtPassword.Text;
 userToUpdate.FullName = txtFullName.Text; userToUpdate.Age =Convert.ToInt32(txtAge.Text);
userToUpdate.PhoneNumber = txtPhone.Text; RefreshGrid();
 } 
else
 { 
MessageBox.Show("Người dùng không tồn tại."); 
}
 }
private void btnDelete_Click(object sender, EventArgs e)
 { 
// Xóa người dùng
 string username = txtUsername.Text;
 User userToDelete = users.FirstOrDefault(u => u.Username == username); 
if (userToDelete != null) { users.Remove(userToDelete); RefreshGrid(); 
} 
else 
{ MessageBox.Show("Người dùng không tồn tại."); }
 }
private void btnSearch_Click(object sender, EventArgs e)
 { 
// Tìm kiếm người dùng string username = txtUsername.Text; 
User user = users.FirstOrDefault(u => u.Username == username); 
if (user != null) {
 txtPassword.Text = user.Password;
txtFullName.Text = user.FullName; 
txtAge.Text = user.Age.ToString(); txtPhone.Text = user.PhoneNumber; 
} 
else 
{
MessageBox.Show("Người dùng không tồn tại."); 
} 
} 
private void RefreshGrid()
 { 
// Cập nhật DataGridView hiển thị thông tin người dùng	
