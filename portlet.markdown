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
