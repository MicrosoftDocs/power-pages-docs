Similar to <https://learn.microsoft.com/en-us/power-pages/admin/power-platform-admin-center> we should have a left nav for Analytics curity of websites

## Monitor traffic to your websites

You can now use the Power Platform admin center to monitor the traffic to the websites in your tenant. You can also see key information such as how many sites have Web Application Firewall disabled, how many sites have external authentication enabled, etc.

## Traffic analytics for all websites in a tenant

1.  Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

2.  On the left pane, select **Resources**, and then select **Power Pages sites**.

3.  Go to 'Analytics'

![A screenshot of a computer Description automatically generated](media/image1.png)

Here you can find the traffic that your websites are receiving: DAU (Daily Active Users), WAU (Weekly Active Users) and MAU (Monthly Active Users)

All charts show the DAU, WAU and MAU across all the sites in the selected environment. You can select the environment of your interest using the drop down.

![A white and purple rectangle Description automatically generated](media/image2.png)

Within the selected environment, you can also select a specific site for which you want to see the traffic. This can be done by selecting the Site ID from the drop down (You can select multiple sites by using ctrl + click)

![A screenshot of a computer Description automatically generated](media/image3.png)

Note: Currently only Site ID is supported for filtering. The Site ID can be found under the 'Your Sites' tab.

### Authenticated and Anonymous User Analytics

The charts show DAU, WAU and MAU numbers for the following categories of users:

1.  Authenticated Users shows the unique authenticated users who accessed the websites.

2.  Anonymous Users shows the unique anonymous users who accessed the websites.

3.  All Users shows the unique users who accessed the websites (either by authentication or anonymously)

Important Note: All the traffic numbers (DAU, WAU and MAU) shown are with the intent of understanding the visits to the websites. The authenticated user counts may vary slightly from license consumption reports. For e.g., in cases where the authenticated user already has a Power Apps license, the visit will NOT be counted in license consumption, but will be counted in the total authenticated users visiting the website.

Important Note: The usage numbers can be under reported for the first few days after enabling the feature. For e.g., the monthly active users will be accurate after 30 days of this feature being live, and weekly active users will be accurate after 7 days of this feature being live.

Who can access these reports?

### Who can view the analytics dashboard?

To access the security dashboard, you should have one of the following roles:

1.  Global Administrator

2.  Dynamics 365 administrator

3.  Power Platform administrator

4.  System administrator

Note: System administrators can see only the environments for which they are a System Administrator.
