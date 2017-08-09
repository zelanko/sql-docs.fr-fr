---
title: "Mise en route avec le contrôle ReportViewer 2016 | Documents Microsoft"
ms.custom: 
ms.date: 06/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01a821c4-2920-400c-be03-93d26c749bb1
caps.latest.revision: 12
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a6a0bbee9141df565966df3e90f396e33c9b96a7
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="integrating-reporting-services-using-reportviewer-controls---get-started"></a>Intégration de Reporting Services à l’aide de contrôles ReportViewer - mise en route

Découvrez comment les développeurs peuvent incorporer des rapports paginés dans des sites web ASP.Net et les applications Windows forms, via le contrôle de ReportViewer Reporting Services 2016. Vous pouvez ajouter le contrôle à un nouveau projet, ou mettre à jour un projet existant.

## <a name="adding-the-reportviewer-control-to-a-new-web-project"></a>Ajout du contrôle ReportViewer pour un projet web

1. Créer un nouveau **Site Web ASP.NET vide** ou ouvrez un projet ASP.NET existant.

    ![Créer-nouvelle-ASPNET-projet ssRS](../../reporting-services/application-integration/media/ssrs-create-new-aspnet-project.png)

2. Installez le package de nuget du contrôle ReportViewer 2016 via la **console du Gestionnaire de package Nuget**.

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WebForms
    ```
3. Ajouter une nouvelle page .aspx au projet et inscrire l’assembly du contrôle ReportViewer pour une utilisation dans la page.

    ```
    <%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>
    ```
    
4. Ajouter un **ScriptManagerControl** à la page.

5. Ajouter le contrôle ReportViewer à la page. L’extrait de code ci-dessous peut être mis à jour pour faire référence à un rapport hébergé sur un serveur de rapports à distance.

    ```
    <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
      <ServerReport ReportPath="" ReportServerUrl="" />
    </rsweb:ReportViewer>
    ```
    
La dernière page doit ressembler à ce qui suit.

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="Sample" %>

<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

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
            <ServerReport ReportServerUrl="http://AContosoDepartment/ReportServer" ReportPath="/LatestSales" />
        </rsweb:ReportViewer>
    </form>
</body>
</html>

```

## <a name="updating-an-existing-project-to-use-the-reportviewer-control"></a>Mise à jour d’un projet existant pour utiliser le contrôle ReportViewer

Pour utiliser le contrôle ReportViewer 2016 dans un projet existant, ajoutez le contrôle via Nuget et mettre à jour les références d’assembly vers la version *14.0.0.0*. Cela inclut la mise à jour web.config du projet et toutes les pages .aspx qui référencent le contrôle ReportViewer.

### <a name="sample-webconfig-changes"></a>Exemple web.config change

```
<?xml version="1.0"?>
<!--
  For more information on how to configure your ASP.NET application, please visit
  http://go.microsoft.com/fwlink/?LinkId=169433
  -->
<configuration>
  <system.web>
    <compilation debug="true" targetFramework="4.5.2">
      <assemblies>
        <!-- All assemblies updated to version 14.0.0.0. -->
        <add assembly="Microsoft.ReportViewer.Common, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.DataVisualization, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.Design, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.ProcessingObjectModel, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebDesign, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WinForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </assemblies>
      <buildProviders>
        <!-- Version updated to 14.0.0.0. -->
        <add extension=".rdlc"
          type="Microsoft.Reporting.RdlBuildProvider, Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </buildProviders>
    </compilation>
    <httpRuntime targetFramework="4.5.2"/>
    <httpHandlers>
      <!-- Version updated to 14.0.0.0 -->
      <add path="Reserved.ReportViewerWebControl.axd" verb="*"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"
        validate="false"/>
    </httpHandlers>
  </system.web>
  <system.webServer>
    <validation validateIntegratedModeConfiguration="false"/>
    <modules runAllManagedModulesForAllRequests="true"/>
    <handlers>
      <!-- Version updated to 14.0.0.0 -->
      <add name="ReportViewerWebControlHandler" verb="*" path="Reserved.ReportViewerWebControl.axd" preCondition="integratedMode"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
    </handlers>
  </system.webServer>
</configuration>
```

### <a name="sample-aspx"></a>Exemple .aspx

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SampleAspx" %>

<!-- Update version to 14.0.0.0 -->
<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>
```

## <a name="adding-the-reportviewer-control-to-a-new-windows-forms-project"></a>Ajout du contrôle ReportViewer pour un projet Windows forms

1. Créer un nouveau **Application Windows Forms** ou ouvrez un projet existant.

    ![Créer-nouvelle-winforms-projet ssRS](../../reporting-services/application-integration/media/ssrs-create-new-winforms-project.png)

2. Installez le package de nuget du contrôle ReportViewer 2016 via la **console du Gestionnaire de package Nuget**.

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WinForms
    ```
3. Ajouter un nouveau contrôle à partir du code ou [ajouter le contrôle à la boîte à outils](##adding-control-to-visual-studio-toolbar).

    ```
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

## <a name="how-to-set-100-height-on-the-report-viewer-2016-control"></a>Comment définir la hauteur de 100 % sur le contrôle 2016 de visionneuse de rapports

Le nouveau contrôle 2016 de visionneuse de rapports est optimisé pour les pages en mode de normes de HTML5 et fonctionne sur tous les navigateurs modernes. Dans le passé, avec l’ancien contrôle RVC, lorsque vous définissez la propriété de hauteur de 100 %, cela a fonctionné même si aucun des ancêtres avait la hauteur spécifiée. Ce comportement a changé dans HTML5. Lorsque vous définissez cette propriété sur le nouveau contrôle RVC, il fonctionnera correctement que si l’élément parent possède une hauteur définie, autrement dit, pas la valeur auto ou tous les ancêtres de RVC offrent de hauteur de 100 %.

Voici les deux exemples pour ce faire.

### <a name="by-setting-the-height-of-all-the-parent-elements-to-100"></a>En définissant la hauteur du parent tous les éléments à 100 %

```
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
            <ServerReport ReportServerUrl="http://test/ReportServer" ReportPath="/testreport" />
        </rsweb:ReportViewer>
    </div>
    </form>
</body>
</html>

```

### <a name="by-setting-the-style-height-attribute-on-the-parent-of-the-reportviewer-control"></a>En définissant l’attribut de hauteur de style sur le parent du contrôle reportviewer

Pour plus d’informations sur les longueurs de pourcentage de la fenêtre d’affichage, consultez [longueurs de pourcentage de la fenêtre d’affichage](https://www.w3.org/TR/css3-values/#viewport-relative-lengths).

```
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
</head>
<body>
    <form id="form1" runat="server">
    <div style="height:100vh;">
            <asp:ScriptManager runat="server"></asp:ScriptManager>
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote" Height="100%" Width="100%">
            <ServerReport ReportServerUrl="http://test/ReportServer" ReportPath="/testreport" />
        </rsweb:ReportViewer>
    </div>
    </form>
</body>
</html>

```

## <a name="adding-control-to-visual-studio-toolbar"></a>Ajout du contrôle de barre d’outils de Visual Studio

Le contrôle Visionneuse de rapports est désormais fourni comme package NuGet. Pour cette raison, vous ne verrez pas le contrôle Visionneuse de rapports s’affichent dans la boîte à outils Visual Studio par défaut. Vous pouvez ajouter le contrôle à la boîte à outils en procédant comme suit.

1. Installez le package NuGet pour les Windows Forms ou WebForms comme indiqué ci-dessus.

2. Supprimez le contrôle ReportViewer qui est répertorié dans la boîte à outils. Il s’agit du contrôle avec une version de 12.x.

    ![ssRS-supprimer-old-rvcontrol-boîte à outils](../../reporting-services/application-integration/media/ssrs-remove-old-rvcontrol-toolbox.png)

3. Avec le bouton droit cliquez n’importe où dans la boîte à outils, puis sélectionnez **choisir des éléments...** .

    ![ssRS-élément boîte à outils-choisissez](../../reporting-services/application-integration/media/ssrs-toolbox-choose-item.png)
    
4. Sur le **composants .NET Framework**, sélectionnez **Parcourir**.

    ![parcours de boîte à outils de ssRS](../../reporting-services/application-integration/media/ssrs-toolbox-browse.png)

5. Sélectionnez le **Microsoft.ReportViewer.WinForms.dll** ou **Microsoft.ReportViewer.WebForms.dll** à partir du package NuGet que vous avez installé.

    > [!NOTE] 
    > Le package NuGet est installé dans le répertoire de solution de votre projet. Le chemin d’accès à la dll sera semblable au suivant : `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.Winforms.{version}\lib\net40` ou `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.WebForms.{version}\lib\net40`.

6. Le nouveau contrôle doit s’afficher dans la boîte à outils. Vous pouvez ensuite la déplacer sur un autre onglet dans la boîte à outils si vous le souhaitez.

    ![ssRS-boîte à outils-rvcontrol](../../reporting-services/application-integration/media/ssrs-toolbox-rvcontrol.png)

### <a name="things-to-be-aware-of"></a>Éléments à connaître

- Cette opération ajoute une référence pour le package NuGet installé dans votre projet en cours. L’élément dans la boîte à outils est conservées à d’autres projets. Lorsque vous installez le package NuGet dans un nouvelle solution/projet, l’élément de boîte à outils peut faire référence à une version antérieure. 

- Le contrôle doit rester dans la boîte à outils, même si l’assembly n’est plus disponible. Si ce projet a été supprimé, Visual Studio génère une erreur si vous essayez et ajoutez le contrôle de la boîte à outils. Pour corriger cette erreur, supprimez le contrôle à partir de la boîte à outils et ajoutez-le de nouveau à l’aide de la procédure ci-dessus.


## <a name="common-issues"></a>Problèmes courants
    
- Le contrôle ReportViewer 2016 est conçu pour être utilisé avec les navigateurs modernes. Le contrôle peut ne pas fonctionne si les navigateurs restituent la page web dans un mode de compatibilité Internet Explorer. Les sites intranet peuvent nécessiter une balise meta pour remplacer le paramètre qui encourager le rendu des pages de l’intranet en mode de compatibilité.

    ```
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    ```
      
## <a name="providing-feedback"></a>Envoi de commentaires

Informer l’équipe de problèmes rencontrés avec le contrôle sur le [forums MSDN de Services Reporting](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlreportingservices) ou par courrier électronique en [ RVCFeedback@microsoft.com ](mailto:RVCFeedback@microsoft.com).

## <a name="see-also"></a>Voir aussi

[Collecte de données dans le contrôle de ReportingViewer 2016](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-data-collection.md)  
D’autres questions ? [Essayez le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)


