## # All Portlet Property in ```@Component``` section.

```
@Component(
	property = {
		"com.liferay.portlet.display-category=category.sample",
		"javax.portlet.display-name=P1Z2 Portlet",
		"javax.portlet.init-param.config-template=/configuration.jsp",
		"javax.portlet.init-param.view-template=/view.jsp",
		"javax.portlet.name=com_acme_p1z2_web_internal_portlet_P1Z2Portlet",
                "javax.portlet.resource-bundle=content.Language",
		"javax.portlet.supported-locale=en_US,ja,pt_BR"
	},
	service = Portlet.class
)

```

### # Add the bnd Instruction for Language module in Liferay

```
-liferay-aggregate-resource-bundles: com.acme.u8t2.impl
```
