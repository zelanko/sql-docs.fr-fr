---
title: "Gestionnaire de connexions OData | Microsoft Docs"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
caps.latest.revision: 9
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# Gestionnaire de connexions OData
  Utilisez un gestionnaire de connexions OData pour vous connecter à une source OData. Un composant source OData se connecte à une source OData à l’aide d’un gestionnaire de connexions OData et consomme les données du service. Pour plus d'informations, consultez [OData Source](../../integration-services/data-flow/odata-source.md).  
  
## <a name="adding-an-odata-connection-manager-to-an-ssis-package"></a>Ajout d’un gestionnaire de connexions OData à un package SSIS  
 Vous pouvez ajouter un nouveau gestionnaire de connexions OData à un package SSIS de trois manières :  
  
-   Cliquez sur le bouton **Nouveau…** dans **Éditeur de source OData**  
  
-   Cliquez avec le bouton droit sur le dossier **Gestionnaires de connexions** dans **l’Explorateur de solutions**, puis cliquez sur **Nouveau gestionnaire de connexions**. Sélectionnez **ODATA** pour **Type du gestionnaire de connexions**.  
  
-   Cliquez avec le bouton droit dans le volet **Gestionnaires de connexions** au bas du concepteur de packages, puis sélectionnez **Nouvelle connexion**. Sélectionnez **ODATA** pour **Type du gestionnaire de connexions**.  
  
## <a name="connection-manager-authentication"></a>Authentification du gestionnaire de connexions  
 Le gestionnaire de connexions OData prend en charge cinq modes d’authentification.  
  
-   Authentification Windows  
  
-   Authentification de base (avec nom d’utilisateur et mot de passe)  

-   Microsoft Dynamics AX Online (avec nom d’utilisateur et mot de passe)
  
-   Microsoft Dynamics CRM Online (avec nom d’utilisateur et mot de passe)
  
-   Microsoft Online Services (avec nom d’utilisateur et mot de passe)  
  
 Pour un accès anonyme, sélectionnez l’option Authentification Windows.  
  
### <a name="specifying-and-securing-credentials"></a>Spécification des informations d'identification  
 Si votre service OData requiert l’authentification de base, spécifiez un nom d’utilisateur et un mot de passe dans [OData Connection Manager Editor](../../integration-services/connection-manager/odata-connection-manager-editor.md). Les valeurs que vous entrez dans l'éditeur sont conservées dans le package. La valeur du mot de passe est chiffrée selon le niveau de protection du package.  
  
 Il existe plusieurs façons de paramétrer les valeurs nom d’utilisateur et mot de passe ou de les stocker en dehors du package. Vous pouvez par exemple utiliser les paramètres ou définir directement les propriétés du gestionnaire de connexions lorsque vous exécutez le package en utilisant SQL Server Management Studio.  
  
## <a name="odata-connection-manager-properties"></a>Propriétés du gestionnaire de connexions OData  
 Le tableau suivant répertorie les propriétés du gestionnaire de connexions OData.  
  
|||  
|-|-|  
|Propriété|Description|  
|Url|URL vers le document de service.|  
|UserName|Nom d'utilisateur à utiliser pour l'authentification de base.|  
|Mot de passe|Mot de passe à utiliser pour l'authentification de base.|  
|ConnectionString|Reflète d'autres propriétés du gestionnaire de connexions.|  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur du gestionnaire de connexions OData](../../integration-services/connection-manager/odata-connection-manager-editor.md)  
  
  