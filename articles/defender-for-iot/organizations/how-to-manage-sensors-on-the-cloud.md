---
title: Manage sensors with Defender for IoT in the Azure portal
description: Learn how to onboard, view, and manage sensors with Defender for IoT in the Azure portal.
ms.date: 11/09/2021
ms.topic: how-to
---

# Manage sensors with Defender for IoT in the Azure portal

This article describes how to onboard, view, and manage sensors with [Defender for IoT in the Azure portal](https://portal.azure.com/#blade/Microsoft_Azure_IoT_Defender/IoTDefenderDashboard/Getting_Started).

## Onboard sensors

You onboard a sensor by registering it with Microsoft Defender for IoT and downloading a sensor activation file.

### Register the sensor

**To register:**

1. Go to the [Defender for IoT: Getting started page](https://portal.azure.com/#blade/Microsoft_Azure_IoT_Defender/IoTDefenderDashboard/Getting_Started) in the Azure portal.

1. Select **Onboard sensor**.

   :::image type="content" source="media/how-to-manage-sensors-on-the-cloud/onboard-a-sensor.png" alt-text="Select onboard sensor to start the onboarding process for your sensor.":::

1. Create a sensor name. 

    We recommend that you include the IP address of the sensor you installed as part of the name, or use an easily identifiable name. This ensures easier tracking and consistent naming between the registration name in the [Azure portal](https://portal.azure.com/#blade/Microsoft_Azure_IoT_Defender/IoTDefenderDashboard/Getting_Started) and the IP of the deployed sensor displayed in the sensor console.

1. Associate the sensor with an Azure subscription.

    :::image type="content" source="media/how-to-manage-sensors-on-the-cloud/name-subscription.png" alt-text="Enter a meaningful name, and connect your sensor to a subscription.":::

1. Choose a sensor connection mode by using the **Cloud connected** toggle. If the toggle is on, the sensor is cloud connected. If the toggle is off, the sensor is locally managed.

   - **Cloud-connected sensors**: Information that the sensor detects is displayed in the sensor console. Alert information is delivered through an IoT hub and can be shared with other Azure services, such as Microsoft Sentinel. In addition, threat intelligence packages can be pushed from Defender for IoT to sensors. Conversely when, the sensor is not cloud connected, you must download  threat intelligence packages and then upload them to your enterprise sensors. To allow Defender for IoT to push packages to sensors, enable the **Automatic Threat Intelligence Updates** toggle. For more information, see [Threat intelligence research and packages](how-to-work-with-threat-intelligence-packages.md).
   
   For cloud connected sensors, the name defined during onboarding is the name that appears in the sensor console. You can't change this name from the console directly. For locally managed sensors, the name applied during onboarding will be stored in Azure but can be updated in the sensor console.

   - **Locally managed sensors**: Information that sensors detect is displayed in the sensor console. If you're working in an air-gapped network and want a unified view of all information detected by multiple locally managed sensors, work with the on-premises management console.

1. Select a site to associate your sensor to within an IoT Hub. The IoT Hub will serve as a gateway between this sensor and Microsoft Defender for IoT. Define the display name, and zone. You can also add descriptive tags. The display name, zone, and tags are descriptive entries on the [Sites and Sensors page](#view-onboarded-sensors).

1. Select **Register**. 

### Download the sensor activation file

After registering a sensor you will be able to download an activation file. The sensor activation file contains instructions about the management mode of the sensor. You download a unique activation file for each sensor that you deploy. A user who signs in to the sensor console for the first time uploads the activation file to the sensor.

**To download an activation file:**

1. On the **Onboard Sensor** page, select **Register**

1. Select **download activation file**.

1. Make the file accessible to the user who's signing in to the sensor console for the first time.

## View onboarded sensors

To view important operational information about onboarded sensors:

1. Go to [Defender for IoT: Getting started](https://portal.azure.com/#blade/Microsoft_Azure_IoT_Defender/IoTDefenderDashboard/Getting_Started), in the Azure portal.

1. Select **Sites and Sensors**. The page shows how many sensors were onboarded, the number of sensors that are cloud connected and locally managed, as well as:

    :::image type="content" source="media/how-to-manage-sensors-on-the-cloud/sites-and-sensors.png" alt-text="Select the sites and sensors page to view all of the associated sensors.":::

    - The sensor name assigned during onboarding.
    - The connection type (cloud connected or locally managed).
    - The zone associated with the sensor.
    - The sensor version installed.
    - The sensor connection status to the cloud.
    - The last time the sensor was detected connecting to the cloud.

## Manage onboarded sensors

Use the [Azure portal](https://portal.azure.com/#blade/Microsoft_Azure_IoT_Defender/IoTDefenderDashboard/Getting_Started) for management tasks related to sensors.

Onboarded sensors can be viewed on the **Sites and Sensors** page. You can also edit sensor information from this page.

### Export sensor details

To export onboarded sensor information, select the **Export** icon on the top of the **Sites and Sensors** page.

:::image type="content" source="media/how-to-manage-sensors-on-the-cloud/export-sensors.png" alt-text="Select the export button to export sensor information.":::

### Edit sensor zone details

Use the **Sites and Sensors** edit options to edit the sensor name and zone.

**To edit:**

1. Select the **ellipsis** (**...**) for the sensor you want to edit.

1. Select **Edit**.

1. Update the sensor zone, or create a new zone.

### Delete a sensor

If you delete a cloud-connected sensor, information won't be sent to the IoT hub. Delete locally connected sensors when you're no longer working with them.

**To delete a sensor:**

1. Select the ellipsis (**...**) for the sensor you want to delete.

1. Select **delete sensor**.

### Reactivate a sensor 

You may need to reactivate your sensor because you want to:

- **Work in cloud-connected mode instead of locally managed mode**: After reactivation, sensor detections are displayed in the sensor and newly detected alert information is delivered through the IoT hub. This information can be shared with other Azure services, such as Microsoft Sentinel.

- **Work in locally managed mode instead of cloud-connected mode**: After reactivation, sensor detection information is displayed only in the sensor.

- **Associate the sensor to a new IoT hub**:  To do this, re-register the sensor with a new hub, and then download a new activation file.

**To reactivate a sensor:**

1. Go to **Sites and Sensors** page in the [Azure portal](https://portal.azure.com/#blade/Microsoft_Azure_IoT_Defender/IoTDefenderDashboard/Getting_Started).

1. Select the sensor for which you want to upload a new activation file.

1. Select the **ellipsis** (**...**), and then select **delete sensor**.

    :::image type="content" source="media/how-to-manage-sensors-on-the-cloud/delete-a-sensor.png" alt-text="Select the ellipsis and then delete sensor.":::

1. [Onboard the sensor](#onboard-sensors) again in the new mode, or with a new IoT hub by selecting **Onboard a sensor** from the Getting Started page.

1. Download the activation file.

1. Sign in to the Defender for IoT sensor console.

1. In the sensor console, select **System settings** > **Sensor management** > **Subscription & Activation Mode**.

1. Select **Select file** choose the file you saved from the Onboard sensor page.

1. Select **Activate**.

## Next steps

[Activate and set up your sensor](how-to-activate-and-set-up-your-sensor.md)
