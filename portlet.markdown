### #Handling the mvcPath Portlet Parameter
```
@Override
public void render(
		RenderRequest renderRequest, RenderResponse renderResponse)
	throws IOException, PortletException {

	if (_log.isInfoEnabled()) {
		String mvcPath = renderRequest.getParameter("mvcPath");

		_log.info("MVC path " + mvcPath);
	}

	super.render(renderRequest, renderResponse);
}

private static final Log _log = LogFactoryUtil.getLog(C8M3Portlet.class);

```
### # Examine the Portlet’s Action-Handling Methods

```
@Component(
	property = {
		"com.liferay.portlet.display-category=category.sample",
		"javax.portlet.display-name=U8T2 Portlet",
		"javax.portlet.init-param.view-template=/view.jsp"
	},
	service = Portlet.class
)
public class U8T2Portlet extends MVCPortlet {

	public void doSomething(
		ActionRequest actionRequest, ActionResponse actionResponse) {

		if (_log.isInfoEnabled()) {
			_log.info("Invoking #doSomething(ActionRequest, ActionResponse)");
		}
	}

	public void doSomethingElse(
		ActionRequest actionRequest, ActionResponse actionResponse) {

		if (_log.isInfoEnabled()) {
			_log.info(
				"Invoking #doSomethingElse(ActionRequest, ActionResponse)");
		}
	}

	@ProcessAction(name = "nameForTheDoSomethingMoreMethod")
	public void doSomethingMore(
		ActionRequest actionRequest, ActionResponse actionResponse) {

		if (_log.isInfoEnabled()) {
			_log.info(
				"Invoking #doSomethingMore(ActionRequest, ActionResponse)");
		}
	}

	private static final Log _log = LogFactoryUtil.getLog(U8T2Portlet.class);

}

```
### # JSP

```
<%@ taglib uri="http://java.sun.com/portlet_2_0" prefix="portlet" %>

<portlet:actionURL name="doSomething" var="actionURL" />

<h4>U8T2 Portlet</h4>

<p>
	<a href="<%= actionURL %>">Do Something</a>
</p>

<p>
	<a href="<portlet:actionURL name="doSomethingElse" />">Do Something Else</a>
</p>

<p>
	<a href="<portlet:actionURL><portlet:param name="javax.portlet.action" value="nameForTheDoSomethingMoreMethod" /></portlet:actionURL>">Do Something More</a>
</p>

```
