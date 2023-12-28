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

### # Tag Libraries
You have access to a powerful set of taglibs for creating commonly used UI components in your apps, themes, and web content. The following taglibs are covered in this section:

AUI: create common UI components such as forms, buttons, and more.

Chart: visualize data. Create bar charts, line charts, scatter charts, spline charts, and much more.

Clay: create Clay components, such as alerts, buttons, drop-down menus, form elements, and more for your apps.

Frontend: create UI components commonly used throughout Portal’s apps, such as add menus, cards, management bars, and more.

Liferay UI: create common UI components such as icons, tabs, and more.

Liferay Util: load additional resources, define parameters, buffer content, and more.

### # Note

Each taglib is available as a FreeMarker macro, except for the Chart taglib. The Chart taglib is not available as a FreeMarker macro. The articles in this section provide the proper syntax to use for each macro. See the FreeMarker Taglib Mappings reference for a complete list of the available FreeMarker taglib macros.
