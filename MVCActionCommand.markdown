### # Examine the Portlet Action URLs
```
<%@ taglib uri="http://java.sun.com/portlet_2_0" prefix="portlet" %>

<h4>L6Y9 Portlet</h4>

<p>
	<a href="<portlet:actionURL name="/l6y9/do_l6y9_able" />">Do L6Y9 Able</a>
</p>

<p>
	<a href="<portlet:actionURL name="/l6y9/do_l6y9_baker" />">Do L6Y9 Baker</a>
</p>

```
### # Examine the MVCActionCommand Classes

```
@Component(
	property = {
		"javax.portlet.name=com_acme_l6y9_web_internal_portlet_L6Y9Portlet",
		"mvc.command.name=/l6y9/do_l6y9_able"
	},
	service = MVCActionCommand.class
)
public class DoL6Y9AbleMVCActionCommand extends BaseMVCActionCommand {

	@Override
	protected void doProcessAction(
		ActionRequest actionRequest, ActionResponse actionResponse) {

		if (_log.isInfoEnabled()) {
			_log.info(
				"Invoking #doProcessAction(ActionRequest, ActionResponse)");
		}
	}

	private static final Log _log = LogFactoryUtil.getLog(
		DoL6Y9AbleMVCActionCommand.class);


```

### # You can associate an MVCActionCommand component with multiple portlets by declaring separate javax.portlet.name properties for each portlet:

```
  @Component(
     property = {
        "javax.portlet.name=com_acme_l6y9_web_internal_portlet_L6Y9Portlet",
        "javax.portlet.name=com_acme_l6y9_web_internal_portlet_L6Y0Portlet",
        "mvc.command.name=/l6y9/download"
     },
     service = MVCActionCommand.class
  )

```

## # MVC Render Command

MVCRenderCommands bind to a portlet by the portlet’s name (e.g., the portlet component javax.portlet.name property value)

```
@Component(
	property = {
		"javax.portlet.name=com_acme_a4p1_web_internal_portlet_A4P1Portlet",
		"mvc.command.name=/a4p1/able"
	},
	service = MVCRenderCommand.class
)
public class A4P1AbleMVCRenderCommand implements MVCRenderCommand {

	@Override
	public String render(
		RenderRequest renderRequest, RenderResponse renderResponse) {

		if (_log.isInfoEnabled()) {
			_log.info("Invoking #render(RenderRequest, RenderResponse)");
		}

		return "/a4p1/able.jsp";
	}

	private static final Log _log = LogFactoryUtil.getLog(
		A4P1AbleMVCRenderCommand.class);

}

```

You can associate an MVCRenderCommand component with multiple portlets by declaring separate javax.portlet.name properties for each portlet:

```
  @Component(
     property = {
        "javax.portlet.name=com_acme_a4p1_web_internal_portlet_A4P1Portlet",
        "javax.portlet.name=com_acme_a4p1_web_internal_portlet_A4P2Portlet",
        "mvc.command.name=/a4p1/download"
     },
     service = MVCRenderCommand.class
  )

```
```
<%@ taglib uri="http://java.sun.com/portlet_2_0" prefix="portlet" %>

<h4>A4P1 Portlet</h4>

<h5>Able</h5>

<portlet:renderURL var="bakerURL">
	<portlet:param name="mvcRenderCommandName" value="/a4p1/baker" />
</portlet:renderURL>

<a href="<%= bakerURL %>">Go to Baker</a>

```

## # MVC Resource Command

MVCResourceCommands bind to a portlet by the portlet’s name (e.g., the portlet component javax.portlet.name property value)

### # Examine the MVCResourceCommand Class

```
@Component(
	property = {
		"javax.portlet.name=com_acme_p8v5_web_internal_portlet_P8V5Portlet",
		"mvc.command.name=/p8v5/download"
	},
	service = MVCResourceCommand.class
)
public class P8V5DownloadMVCResourceCommand implements MVCResourceCommand {

	@Override
	public boolean serveResource(
			ResourceRequest resourceRequest, ResourceResponse resourceResponse)
		throws PortletException {

		try {
			PortletResponseUtil.sendFile(
				resourceRequest, resourceResponse, "p8v5.txt",
				"Hello P8V5!".getBytes(), "text");

			return false;
		}
		catch (IOException ioException) {
			_log.error(ioException, ioException);

			return true;
		}
	}

	private static final Log _log = LogFactoryUtil.getLog(
		P8V5DownloadMVCResourceCommand.class);

}

```

You can associate an MVCResourceCommand component with multiple portlets by declaring separate javax.portlet.name properties for each portlet:

```
  @Component(
     property = {
        "javax.portlet.name=com_acme_p8v5_web_internal_portlet_P8V5Portlet",
        "javax.portlet.name=com_acme_p8v5_web_internal_portlet_P8V6Portlet",
        "mvc.command.name=/p8v5/download"
     },
     service = MVCResourceCommand.class
  )

```

Examine the Portlet Resource URL

```
<%@ taglib uri="http://java.sun.com/portlet_2_0" prefix="portlet" %>

<h4>P8V5 Portlet</h4>

<a href="<portlet:resourceURL id="/p8v5/download" />">Download</a>

```
### # Portlet Preferences

Click the portlet’s options icon (options icon) and click Configuration. The portlet’s preferences window opens.

```
<portlet:defineObjects />

<liferay-portlet:actionURL portletConfiguration="<%= true %>" var="configurationActionURL" />

<aui:form action="<%= configurationActionURL %>" method="post" name="fm">
	<aui:input name="<%= Constants.CMD %>" type="hidden" value="<%= Constants.UPDATE %>" />

	<liferay-portlet:renderURL portletConfiguration="<%= true %>" var="configurationRenderURL" />

	<aui:input name="redirect" type="hidden" value="<%= configurationRenderURL %>" />

	<aui:fieldset>
		<aui:select label="color" name="color" value='<%= (String)portletPreferences.getValue("color", "blue") %>'>
			<aui:option label="Blue" value="blue" />
			<aui:option label="Red" value="red" />
			<aui:option label="Yellow" value="yellow" />
		</aui:select>
	</aui:fieldset>

	<aui:button-row>
		<aui:button type="submit" />
	</aui:button-row>
</aui:form>
```
### # Create the Configuration Action
```
	property = "javax.portlet.name=com_acme_p1z2_web_internal_portlet_P1Z2Portlet",
	service = ConfigurationAction.class
)
public class P1Z2ConfigurationAction extends DefaultConfigurationAction {

	@Override
	public void processAction(
			PortletConfig portletConfig, ActionRequest actionRequest,
			ActionResponse actionResponse)
		throws Exception {

		setPreference(
			actionRequest, "color",
			ParamUtil.getString(actionRequest, "color"));

		super.processAction(portletConfig, actionRequest, actionResponse);
	}

}
```

### # Add the Portlet’s Path Parameters

```
@Component(
	property = {
		"com.liferay.portlet.display-category=category.sample",
		"javax.portlet.display-name=P1Z2 Portlet",
		"javax.portlet.init-param.config-template=/configuration.jsp",
		"javax.portlet.init-param.view-template=/view.jsp",
		"javax.portlet.name=com_acme_p1z2_web_internal_portlet_P1Z2Portlet"
	},
	service = Portlet.class
)
```
