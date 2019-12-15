# Create LAMP stack 
    
	go to folder "lamp_stack" and run command in your terminal
	**docker build -t my_vendor/lamp:1.0 .**
	**docker run -itd -p 80:80 --name test_lamp -h lamp_stack my_vendor/lamp:1.0 bash**
