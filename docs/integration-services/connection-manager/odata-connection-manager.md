---
title: Gestionnaire de connexions OData | Documents Microsoft
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
caps.latest.revision: 9
f1_keywords:
- sql13.dts.designer.odatasource.connectionmanager.f1
- sql13.dts.designer.odataconnectionmanager.f1
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: f54562b59e8c61f723c17e2812ca39cb2e95f273
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="odata-connection-manager"></a>Gestionnaire de connexions OData
 Se connecter à une source de données OData avec un gestionnaire de connexions OData. Un composant OData Source utilise un gestionnaire de connexions OData pour vous connecter à une source de données OData et consommer des données à partir du service. Pour plus d'informations, consultez [OData Source](../../integration-services/data-flow/odata-source.md).  
  
## <a name="adding-an-odata-connection-manager-to-an-ssis-package"></a>Ajout d’un gestionnaire de connexions OData à un package SSIS  
 Vous pouvez ajouter un nouveau gestionnaire de connexions OData à un package SSIS de trois façons :  
  
-   Cliquez sur le bouton **Nouveau…** dans **Éditeur de source OData**  
  
-   Cliquez avec le bouton droit sur le dossier **Gestionnaires de connexions** dans **l’Explorateur de solutions**, puis cliquez sur **Nouveau gestionnaire de connexions**. Sélectionnez **ODATA** pour **Type du gestionnaire de connexions**.  
  
-   Avec le bouton droit dans le **gestionnaires de connexions** volet en bas du concepteur et sélectionnez package **nouvelle connexion**. Sélectionnez **ODATA** pour **Type du gestionnaire de connexions**.  
  
## <a name="connection-manager-authentication"></a>Authentification du gestionnaire de connexions  
 Le Gestionnaire de connexions OData prend en charge cinq modes d’authentification.  
  
-   Authentification Windows  
  
-   Authentification de base (avec nom d’utilisateur et mot de passe)  

-   Microsoft Dynamics AX Online (avec nom d’utilisateur et mot de passe)
  
-   Microsoft Dynamics CRM Online (avec nom d’utilisateur et mot de passe)
  
-   Microsoft Online Services (avec nom d’utilisateur et mot de passe)  
  
Pour un accès anonyme, sélectionnez l’option Authentification Windows.  

Pour se connecter à Microsoft Dynamics AX Online ou Microsoft Dynamics CRM online, vous ne pouvez pas utiliser le **Microsoft Online Services** option d’authentification. Vous ne pouvez pas également utiliser toute option qui est configurée pour l’authentification multifacteur.
  
### <a name="specifying-and-securing-credentials"></a>Spécification des informations d'identification  
 Si votre service OData requiert l’authentification de base, spécifiez un nom d’utilisateur et un mot de passe dans [OData Connection Manager Editor](../../integration-services/connection-manager/odata-connection-manager-editor.md). Les valeurs que vous entrez dans l'éditeur sont conservées dans le package. La valeur du mot de passe est chiffrée selon le niveau de protection du package.  
  
 Il existe plusieurs façons de paramétrer les valeurs nom d’utilisateur et mot de passe ou de les stocker en dehors du package. Par exemple, vous pouvez utiliser des paramètres, ou définir la connexion des propriétés de gestionnaire directement lorsque vous exécutez le package à partir de SQL Server Management Studio.  
  
## <a name="odata-connection-manager-properties"></a>Propriétés du gestionnaire de connexions OData  
 La liste suivante décrit les propriétés du Gestionnaire de connexions OData.  
  
|||  
|-|-|  
|Propriété|Description|  
|Url|URL vers le document de service.|  
|UserName|Nom d’utilisateur à utiliser pour l’authentification, si nécessaire.|  
|Mot de passe|Mot de passe à utiliser pour l’authentification, si nécessaire.|  
|ConnectionString|Inclut d’autres propriétés du Gestionnaire de connexions.|  
  
## <a name="odata-connection-manager-editor"></a>Éditeur du gestionnaire de connexions OData
  Utilisez le **OData Connection Manager Editor** boîte de dialogue pour ajouter une connexion ou de modifier une connexion existante à une source de données OData.  
  
### <a name="options"></a>Options  
 **Nom du gestionnaire de connexions**  
 Nom du gestionnaire de connexions.  
  
 **Emplacement du document de service**  
 URL du service OData. Par exemple : http://services.odata.org/V3/Northwind/Northwind.svc/.  
  
 **Authentification**  
Sélectionnez l'une des options suivantes :
-   **L’authentification Windows**. Pour l’accès anonyme, sélectionnez cette option.
-   **Authentification de base** 
-   **En ligne de Microsoft Dynamics AX** pour Dynamics AX en ligne
-   **Microsoft Dynamics CRM Online** pour Dynamics CRM Online
-   **Microsoft Online Services** pour Microsoft Online Services

Si vous sélectionnez une option autre que l’authentification Windows, entrez le **nom d’utilisateur** et **mot de passe**. 

Pour se connecter à Microsoft Dynamics AX Online ou Microsoft Dynamics CRM online, vous ne pouvez pas utiliser le **Microsoft Online Services** option d’authentification. Vous ne pouvez pas également utiliser toute option qui est configurée pour l’authentification multifacteur.

 **Tester la connexion**  
 Cliquez sur ce bouton pour tester la connexion à la source OData.  

