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
