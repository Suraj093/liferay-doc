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
