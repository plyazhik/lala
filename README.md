package ru.ifmo.javaee;

import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.HttpSession;

/**
 * Servlet implementation class FirstServlet
 */
@WebServlet("/FirstServlet")
public class FirstServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public FirstServlet() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		//*response.getWriter().append("Served at: ").append(request.getContextPath());
		doPost(request, response);
	}
		
	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		String username = request.getParameter("user");
		String password = request.getParameter("password");
		PrintWriter out = response.getWriter();out.println( "<!doctype html public \"-//W3C//DTD HTML 4.0 				Transitional//EN\">\n"
				 + "<html>\n"
				 + "<head>\n"
				 + " <title>Online Shopping</title>\n"
				 + "</head>\n"
			 + "<body>\n");
		int counter = 0;
		if (username.equals("Michael") && password.equals("qwerty")) {
				out.println(username + "Welcome to Online Shopping!" + "<BR>");
					counter = 0;
			/* Создание сеанса для пользователя и сохранение имени пользователя. */
					HttpSession session = request.getSession(true);
					session.setAttribute("user", username);
				} else {
					out.println("Sorry! Invalid username and password");
					counter = 1;
		}
		if (counter == 0) {
			/* Вывод данных пользователю. */
		out.println("<BODY><HTML>");	
		out.println("<HR>");
		out.println("<FORM ACTION = http://localhost:8080/Lab/SecondSessionServlet METHOD=POST>");
		out.println("<TABLE WIDTH=500>");
		out.println("<TR><TH>ITEM NO</TH> <TH>SHIRT TYPE </TH> <TH>BUY</TH> </TR> ");
		out.println("<TR><TD> 1 </TD><TD> PeterEngland  </TD> <TD> <INPUT NAME = c1 TYPE = CHECKBOX VALUE = PeterEngland ></TD> </TR> ");
		out.println("<TR><TD> 2 </TD><TD> Excaliber     </TD> <TD> <INPUT NAME = c2 TYPE = CHECKBOX VALUE = Excaliber ></TD> </TR> ");
		out.println("<TR><TD> 3 </TD><TD> Vaun Newman   </TD> <TD> <INPUT NAME = c3 TYPE = CHECKBOX VALUE = VaunNewman></TD> </TR> ");
		out.println("<TR><TD> 4 </TD><TD> Wills Classic </TD> <TD> <INPUT NAME = c4 TYPE = CHECKBOX VALUE = WillsClassic></TD> </TR> ");
		out.println("</TABLE>");
		out.println("<INPUT TYPE = SUBMIT VALUE = SUBMIT>");
		out.println("</FORM>");
		out.println("</BODY></HTML>");
		out.close();
	}

		doGet (request, response);
	}

}
