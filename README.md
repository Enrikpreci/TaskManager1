# TaskManager1
using System.Web.Mvc;

namespace TaskManager.Controllers
{
    public class HomeController : Controller
    {
        public ActionResult Index()
        {
            return View();
        }
    }
}
@{
    ViewBag.Title = "Home";
    Layout = "~/Views/Shared/_Layout.cshtml";
}

<h2>Welcome to TaskManager</h2>
<p>This is the home page.</p>
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>@ViewBag.Title - TaskManager</title>
</head>
<body>
    <div>
        <h1>TaskManager App</h1>
        <nav>
            <a href="/">Home</a> |
            <a href="/Task">Tasks</a>
        </nav>
        <hr />
        @RenderBody()
    </div>
</body>
</html>

using System.Web.Mvc;
using System.Web.Routing;

namespace TaskManager
{
    public class RouteConfig
    {
        public static void RegisterRoutes(RouteCollection routes)
        {
            routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

            routes.MapRoute(
                name: "Default",
                url: "{controller}/{action}/{id}",
                defaults: new { controller = "Home", action = "Index", id = UrlParameter.Optional }
            );
        }
    }
}
using System.Web.Mvc;
using System.Web.Routing;

namespace TaskManager
{
    public class MvcApplication : System.Web.HttpApplication
    {
        protected void Application_Start()
        {
            AreaRegistration.RegisterAllAreas();
            RouteConfig.RegisterRoutes(RouteTable.Routes);
        }
    }
}
