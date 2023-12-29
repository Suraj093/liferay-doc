
# # Tag Libraries
You have access to a powerful set of taglibs for creating commonly used UI components in your apps, themes, and web content. The following taglibs are covered in this section:

AUI: create common UI components such as forms, buttons, and more.

Chart: visualize data. Create bar charts, line charts, scatter charts, spline charts, and much more.

Clay: create Clay components, such as alerts, buttons, drop-down menus, form elements, and more for your apps.

Frontend: create UI components commonly used throughout Portal’s apps, such as add menus, cards, management bars, and more.

Liferay UI: create common UI components such as icons, tabs, and more.

Liferay Util: load additional resources, define parameters, buffer content, and more.

### # Note

Each taglib is available as a FreeMarker macro, except for the Chart taglib. The Chart taglib is not available as a FreeMarker macro. The articles in this section provide the proper syntax to use for each macro. See the FreeMarker Taglib Mappings reference for a complete list of the available FreeMarker taglib macros.

### # Alloy UI (AUI) Tag Library
```
<%@ taglib prefix="aui" uri="http://liferay.com/tld/aui" %>
https://resources.learn.liferay.com/reference/latest/en/dxp/taglibs/util-taglib/aui/tld-summary.html

```
The AUI taglib is also available via a macro for your FreeMarker theme templates and web content templates. Follow this syntax:
```
<@liferay_aui["tag-name"] attribute="string value" attribute=10 />
```
### # An example form is shown below:
```
<aui:form name="fm">
	<aui:fieldset-group markupView="lexicon">
		<aui:fieldset label="Personal Information">
			<aui:row>
				<aui:col width="50">
					<aui:input label="First Name" name="firstName" type="text" />
				</aui:col>
				<aui:col width="50">
					<aui:input label="Last Name" name="lastName" type="text" />
				</aui:col>
			</aui:row>
			<aui:row>
				<aui:col width="50">
					<aui:input label="Username" name="username" type="text" />
				</aui:col>
				<aui:col width="50">
					<aui:input label="Email" name="email" type="email" />
				</aui:col>
			</aui:row>
		</aui:fieldset>
	</aui:fieldset-group>
	<aui:fieldset-group markupView="lexicon">
		<aui:fieldset label="Miscellaneous">
			<aui:input label="Hobbies" name="hobbies" type="textarea" />
			<aui:input label="Receive email updates" name="emailUpdates" type="checkbox" />
		</aui:fieldset>
	</aui:fieldset-group>
	<aui:button-row>
		<aui:button name="submitButton" type="submit" value="Submit" />
	</aui:button-row>
</aui:form>
```
### # AUI Form Validation
```
<aui:form name="myForm">
    <aui:input name="password" id="password" label="Password"
    required="true" />
    <aui:input name="confirmPassword" id="password"
    label="Confirm Password" required="true">
        <aui:validator name="equalTo"
        errorMessage="The passwords much match. Please try again." >
        '#<portlet:namespace>password'
        </aui:validator>
    </aui:input>
</aui:form>
```
### # Clay Tag Library
```
<%@ taglib prefix="clay" uri="http://liferay.com/tld/clay" %>
https://docs.liferay.com/ce/apps/frontend-taglib/3.0.0/taglibdocs/liferay-clay/button.html
```
The Liferay Clay taglib is also available via a macro for your FreeMarker theme templates and web content templates. Follow this syntax:
```
<@clay["tag-name"] attribute="string value" attribute=10 />
```
Clay taglibs provide the following UI components for your apps:
```
Alerts
Badges
Buttons
Cards
Dropdown Menus and Action Menus
Form Elements
Icons
Labels and links
Management Toolbar
Navigation Bars
Progress Bars
Stickers
```

### # Liferay UI Tag Library
To use the Liferay-UI taglib library in your apps, you must add the following declaration to your JSP:

```
<%@ taglib prefix="liferay-ui" uri="http://liferay.com/tld/ui" %>
https://resources.learn.liferay.com/reference/latest/en/dxp/taglibs/util-taglib/liferay-ui/tld-summary.html
```
The Liferay-UI taglib is also available via a macro for your FreeMarker theme and web content templates. Follow this syntax:

```
<@liferay_ui["tag-name"] attribute="string value" attribute=10 />
```

Code Example
```
<liferay-ui:tabs
    names='<%= "user-settings,display-settings,rss" %>'
    param="tabs2"
    refresh="<%= false %>"
    type="tabs nav-tabs-default"
>
    <liferay-ui:section>
        <%@ include file="/configuration/user_settings.jspf" %>
    </liferay-ui:section>

    <liferay-ui:section>
        <%@ include file="/configuration/display_settings.jspf" %>
    </liferay-ui:section>

    <liferay-ui:section>
        <%@ include file="/configuration/rss.jspf" %>
    </liferay-ui:section>
</liferay-ui:tabs>
```

