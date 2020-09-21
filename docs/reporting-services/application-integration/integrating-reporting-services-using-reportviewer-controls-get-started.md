---
title: Bien démarrer avec les contrôles Visionneuse de rapports
description: Les contrôles Visionneuse de rapports permettent d’intégrer des rapports Reporting Services RDL dans les applications WebForms et WinForms.
ms.custom: seo-lt-2019
ms.date: 09/01/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: conceptual
ms.assetid: 01a821c4-2920-400c-be03-93d26c749bb1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 009c70da7365cc232dc5b00da6b4f1f62bfca8e2
ms.sourcegitcommit: 04fb4c2d7ccddd30745b334b319d9d2dd34325d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89569959"
---
# <a name="integrate-reporting-services-using-the-report-viewer-controls---get-started"></a>Intégrer Reporting Services à l’aide des contrôles Visionneuse de rapports - Prise en main

Les contrôles Visionneuse de rapports permettent d’intégrer des rapports Reporting Services RDL dans les applications WebForms et WinForms. Pour plus d’informations sur les mises à jour récentes, consultez le [journal des modifications](changelog.md).

## <a name="add-the-report-viewer-control-to-a-new-web-project"></a>Ajouter le contrôle Visionneuse de rapports à un nouveau projet web

1. Créez un **site web ASP.NET vide** ou ouvrez un projet ASP.NET existant.

    Vous pouvez utiliser .NET Framework 4.6 ou une version plus récente.

    ![Capture d’écran de la création d’un site Web vide ASP.NET.](../../reporting-services/application-integration/media/ssrs-create-new-aspnet-project-4-6.png)

2. Installez le package NuGet du contrôle Visionneuse de rapports via la **console du gestionnaire de package Nuget**.

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WebForms
    ```
3. Ajoutez une nouvelle page .aspx au projet et inscrivez l’assembly du contrôle Visionneuse de rapports en vue de l’utiliser dans la page.

    ```
    <%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>
    ```
    
4. Ajoutez un **ScriptManagerControl** à la page.

5. Ajoutez le contrôle Visionneuse de rapports à la page. L’extrait de code ci-dessous peut être mis à jour pour référencer un rapport hébergé sur un serveur de rapports à distance.

    ```
    <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
      <ServerReport ReportPath="" ReportServerUrl="" />
    </rsweb:ReportViewer>
    ```
    
La page finale devrait ressembler à ce qui suit.

```html
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="Sample" %>

<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <meta http-equiv="X-UA-Compatible" content="IE=edge" /> 
    <title></title>
</head>
<body>
    <form id="form1" runat="server">
    <asp:ScriptManager runat="server"></asp:ScriptManager>        
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
            <ServerReport ReportServerUrl="https://AContosoDepartment/ReportServer" ReportPath="/LatestSales" />
        </rsweb:ReportViewer>
    </form>
</body>
</html>
```

## <a name="update-an-existing-project-to-use-the-report-viewer-control"></a>Mettre à jour un projet existant pour utiliser le contrôle Visionneuse de rapports

Veillez à mettre à jour les références d’assembly vers la version *15.0.0.0*, y compris le fichier web.config du projet et toutes les pages .aspx qui référencent le contrôle de visionneuse.

### <a name="sample-webconfig-changes"></a>Exemple de modifications apportées au fichier web.config

```xml
<?xml version="1.0"?>
<!--
  For more information on how to configure your ASP.NET application, please visit
  https://go.microsoft.com/fwlink/?LinkId=169433
  -->
<configuration>
  <system.web>
    <compilation debug="true" targetFramework="4.6">
      <assemblies>
        <!-- All assemblies updated to version 15.0.0.0. -->
        <add assembly="Microsoft.ReportViewer.Common, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.DataVisualization, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.Design, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.ProcessingObjectModel, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebDesign, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WinForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </assemblies>
      <buildProviders>
        <!-- Version updated to 15.0.0.0. -->
        <add extension=".rdlc"
          type="Microsoft.Reporting.RdlBuildProvider, Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </buildProviders>
    </compilation>
    <httpRuntime targetFramework="4.6"/>
    <httpHandlers>
      <!-- Version updated to 15.0.0.0 -->
      <add path="Reserved.ReportViewerWebControl.axd" verb="*"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"
        validate="false"/>
    </httpHandlers>
  </system.web>
  <system.webServer>
    <validation validateIntegratedModeConfiguration="false"/>
    <modules runAllManagedModulesForAllRequests="true"/>
    <handlers>
      <!-- Version updated to 15.0.0.0 -->
      <add name="ReportViewerWebControlHandler" verb="*" path="Reserved.ReportViewerWebControl.axd" preCondition="integratedMode"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
    </handlers>
  </system.webServer>
</configuration>
```

### <a name="sample-aspx"></a>Exemple de fichier .aspx

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SampleAspx" %>

<!-- Update version to 15.0.0.0 -->
<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>
```

## <a name="add-the-report-viewer-control-to-a-new-windows-forms-project"></a>Ajouter le contrôle Visionneuse de rapports à un nouveau projet Windows Forms

1. Créez une **application Windows Forms** ou ouvrez un projet existant.

    Vous pouvez utiliser .NET Framework 4.6 ou une version plus récente.
    
    ![Capture d’écran de la création d’une application Windows Forms.](../../reporting-services/application-integration/media/ssrs-create-new-winforms-project-4-6.png)

2. Installez le package NuGet du contrôle Visionneuse de rapports via la **console du gestionnaire de package Nuget**.

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WinForms
    ```
3. Ajoutez un nouveau contrôle à partir du code ou [ajoutez le contrôle à la boîte à outils](#add-the-control-to-visual-studio-toolbar).

    ```csharp
    private Microsoft.Reporting.WinForms.ReportViewer reportViewer1;
    
    private void InitializeComponent()
    {
        this.reportViewer1 = new Microsoft.Reporting.WinForms.ReportViewer();
        this.SuspendLayout();
        // 
        // reportViewer1
        // 
        this.reportViewer1.Location = new System.Drawing.Point(168, 132);
        this.reportViewer1.Name = "reportViewer1";
        this.reportViewer1.ServerReport.BearerToken = null;
        this.reportViewer1.Size = new System.Drawing.Size(396, 246);
        this.reportViewer1.TabIndex = 0;
        // 
        // Form1
        // 
        this.Controls.Add(this.reportViewer1);
    }
    ```

## <a name="how-to-set-100-height-on-the-report-viewer-control"></a>Comment définir une hauteur de 100 % sur le contrôle Visionneuse de rapports

Si vous définissez la hauteur du contrôle de visionneuse à 100 %, l’élément parent doit avoir une hauteur définie ou tous les ancêtres sont obligés d’avoir des pourcentages de hauteur.

### <a name="set-the-height-of-all-the-ancestors-to-100"></a>Définir la hauteur de tous les ancêtres à 100 %

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <style>
        html,body,form,#div1 {
            height: 100%; 
        }
    </style>
   </head>
<body>
    <form id="form1" runat="server">
    <div id="div1" >
            <asp:ScriptManager runat="server"></asp:ScriptManager>
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote" Height="100%" Width="100%">
            <ServerReport ReportServerUrl="https://test/ReportServer" ReportPath="/testreport" />
        </rsweb:ReportViewer>
    </div>
    </form>
</body>
</html>
```

### <a name="set-the-parents-height-attribute"></a>Définir l’attribut de hauteur du parent

Pour plus d’informations sur les longueurs en pourcentage de la fenêtre d’affichage, consultez [Viewport-percentage lengths](http://www.w3.org/TR/css3-values/#viewport-relative-lengths) (Longueurs en pourcentage de la fenêtre d’affichage).

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
</head>
<body>
    <form id="form1" runat="server">
    <div style="height:100vh;">
            <asp:ScriptManager runat="server"></asp:ScriptManager>
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote" Height="100%" Width="100%">
            <ServerReport ReportServerUrl="https://test/ReportServer" ReportPath="/testreport" />
        </rsweb:ReportViewer>
    </div>
    </form>
</body>
</html>
```

## <a name="add-the-control-to-visual-studio-toolbar"></a>Ajouter le contrôle à la barre d’outils de Visual Studio

Le contrôle Visionneuse de rapports est désormais fourni sous forme de package NuGet et ne s’affiche plus dans la boîte à outils Visual Studio par défaut. Vous pouvez ajouter manuellement le contrôle à la boîte à outils.

1. Installez le package NuGet pour WinForms ou WebForms comme indiqué ci-dessus.

2. Supprimez le contrôle Visionneuse de rapports qui est répertorié dans la boîte à outils.

    ![Capture d’écran de la suppression du contrôle ReportViewer.](../../reporting-services/application-integration/media/ssrs-remove-old-rvcontrol-toolbox.png)

3. Cliquez avec le bouton droit n’importe où dans la boîte à outils, puis sélectionnez **Choisir les éléments...**

    ![Capture d’écran de l’option Choisir des éléments dans la boîte à outils.](../../reporting-services/application-integration/media/ssrs-toolbox-choose-item.png)
    
4. Dans **Composants .NET Framework**, sélectionnez **Parcourir**.

    ![Capture d’écran du bouton Parcourir dans la boîte de dialogue Composants .NET Framework.](../../reporting-services/application-integration/media/ssrs-toolbox-browse.png)

5. Sélectionnez **Microsoft.ReportViewer.WinForms.dll** ou **Microsoft.ReportViewer.WebForms.dll** à partir du package NuGet que vous avez installé.

    > [!NOTE] 
    > Le package NuGet est installé dans le répertoire de solution de votre projet. Le chemin de la dll ressemble au suivant : `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.Winforms.{version}\lib\net40` ou `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.WebForms.{version}\lib\net40`.

6. Le nouveau contrôle doit s’afficher dans la boîte à outils. Vous pouvez ensuite le déplacer vers un autre onglet de la boîte à outils si vous le souhaitez.

    ![Capture d’écran du nouveau contrôle ReportViewer dans la boîte à outils.](../../reporting-services/application-integration/media/ssrs-toolbox-rvcontrol.png)

## <a name="common-issues"></a>Problèmes courants
    
Le contrôle de visionneuse est conçu pour les navigateurs modernes. Il peut ne pas fonctionner comme prévu si le navigateur restitue la page en utilisant le mode de compatibilité Internet Explorer. Les sites intranet peuvent nécessiter une balise meta pour remplacer le comportement par défaut du navigateur.

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge" />
```

## <a name="nugetorg-pages"></a>Pages NuGet.org

Voici des liens vers des articles sur le site NuGet.org sur les versions WebForm et WinForm du contrôle de la Visionneuse de rapports :

- Microsoft.ReportingServices.ReportViewerControl.WebForms [https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.WebForms/](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.WebForms/)
- Microsoft.ReportingServices.ReportViewerControl.Winforms [https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.WinForms/](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.WinForms/)


## <a name="forum-feedback"></a>Commentaires sur le forum

Informez l’équipe au sujet des problèmes sur les [forums Reporting Services](https://docs.microsoft.com/answers/topics/sql-server-reporting-services.html).

## <a name="see-also"></a>Voir aussi

[Collecte de données dans le contrôle Visionneuse de rapports](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-data-collection.md)  

