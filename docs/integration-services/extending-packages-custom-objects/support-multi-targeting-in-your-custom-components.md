---
title: "Prise en charge de la fonctionnalité de multi-ciblage dans vos composants personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server (starting with 2016)
ms.assetid: ec611374-16bf-4a56-8fd9-45d3ddd7befc
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 57ac95d7883ce47e1a39d4d50d3f60b968bccf21
ms.contentlocale: fr-fr
ms.lasthandoff: 09/21/2017

---
# <a name="support-multi-targeting-in-your-custom-components"></a>Prend en charge la fonctionnalité de multi-ciblage dans vos composants personnalisés
 Vous pouvez maintenant utiliser le concepteur SSIS dans SQL Server Data Tools (SSDT) pour créer, gérer et exécuter des packages qui ciblent SQL Server 2016, SQL Server 2014 ou SQL Server 2012. Pour obtenir SSDT pour Visual Studio 2015, consultez [télécharger la dernière SQL Server Data Tools](/sql-docs/docs/ssdt/download-sql-server-data-tools-ssdt). 

 Dans l’Explorateur de solutions, cliquez avec le bouton droit sur un projet Integration Services, puis sélectionnez **Propriétés** pour ouvrir les pages de propriétés du projet. Sous l’onglet **Général** de **Propriétés de configuration**, sélectionnez la propriété **TargetServerVersion** , puis choisissez SQL Server 2016, SQL Server 2014 ou SQL Server 2012.  
   
 ![Propriété TargetServerVersion dans la boîte de dialogue Propriétés de projet](../../integration-services/media/targetserverversion2.png "propriété TargetServerVersion dans la boîte de dialogue Propriétés de projet")  
 
 ## <a name="multiple-version-support-and-multi-targeting-for-custom-components"></a>Plusieurs versions prises en charge et le multi-ciblage pour les composants personnalisés
 
Toutes les cinq types d’extensions personnalisées de SSIS prend en charge le multi-ciblage.
-   Gestionnaires de connexions
-   Tâches
-   Énumérateurs
-   Modules fournisseurs d'informations
-   Composants de flux de données

Pour les extensions managées, le concepteur SSIS charge la version de l’extension pour la version cible spécifiée. Exemple :
-   Lorsque la version cible est SQL Server 2012, le concepteur charge la version 2012 de l’extension.
-   Lorsque la version cible est SQL Server 2016, le concepteur charge la version 2016 de l’extension.

Extensions de COM ne gèrent pas la fonctionnalité de multi-ciblage. Le concepteur SSIS charge toujours l’extension COM pour la version actuelle de SQL Server, quelle que soit la version cible spécifiée.

## <a name="add-basic-support-for-multiple-versions-and-multi-targeting"></a>Ajouter la prise en charge élémentaire de plusieurs versions et multi-ciblage

Pour des conseils de base, consultez [mise en route de vos extensions personnalisées de SSIS pour être pris en charge par la prise en charge de plusieurs version de SSDT 2015 pour SQL Server 2016](https://blogs.msdn.microsoft.com/ssis/2016/04/19/getting-your-ssis-custom-extensions-to-be-supported-by-the-multi-version-support-of-ssdt-2015-for-sql-server-2016/). Ce billet de blog décrit les conditions ou les étapes suivantes.

-   Déployer vos assemblys dans les dossiers appropriés.

-   Créer un fichier de mappage d’extension pour SQL Server 2014 et versions haute.

## <a name="add-code-to-switch-versions"></a>Ajoutez du code pour basculer des versions

### <a name="switch-versions-in-a-custom-connection-manager-task-enumerator-or-log-provider"></a>Versions de commutateur dans un gestionnaire de connexions personnalisé, une tâche, un énumérateur ou un module fournisseur d’informations

Pour un gestionnaire de connexions personnalisé, tâche, énumérateur ou fournisseur de journaux, ajouter une logique vers une version antérieure dans le **SaveToXML au** (méthode).

```csharp
public void SaveToXML(XmlDocument doc, IDTSInfoEvents events)
{
    if (TargetServerVersion == DTSTargetServerVersion.SQLServer2014)
    {
        // Add logic to downgrade from SQL Server 2016 to SQL Server 2014.
    }

    if (TargetServerVersion == DTSTargetServerVersion.SQLServer2012)
    {
         // Add logic to downgrade from SQL Server 2016 to SQL Server 2012.
    }
}
```

### <a name="switch-versions-in-a-custom-data-flow-component"></a>Versions de commutateur dans un composant de flux de données personnalisé

Pour un gestionnaire de connexions personnalisé, tâche, énumérateur ou fournisseur de journaux, ajouter une logique de rétrogradation dans le nouveau **PerformDowngrade** (méthode).

```csharp
public override void PerformDowngrade(int pipelineVersion, DTSTargetServerVersion targetServerVersion)
{
    if (targetServerVersion == DTSTargetServerVersion.DTSTSV_SQLSERVER2014)
    {
        // Add logic to downgrade from SQL Server 2016 to SQL Server 2014.
        ComponentMetaData.Version = 8;
    }

    if (targetServerVersion == DTSTargetServerVersion.DTSTSV_SQLSERVER2012)
    {
          // Add logic to downgrade from SQL Server 2016 to SQL Server 2012.
        ComponentMetaData.Version = 6;
    }
}
```

## <a name="common-errors"></a>Erreurs fréquentes

### <a name="invalidcastexception"></a>InvalidCastException

**Message d’erreur.** Impossible d’objet COM de cast de type « System.__ComObject » à l’interface de type 'Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100'. Cette opération a échoué, car l’appel QueryInterface sur le composant COM pour l’interface avec l’IID '{BE8C48A3-155B-4810-BA5C-BDF68A659E9E}' a échoué en raison de l’erreur suivante : interface non pris en charge (Exception de HRESULT : 0 x 80004002 (E_NOINTERFACE)). (Microsoft.SqlServer.DTSPipelineWrap).

**Solution.** Si votre extension personnalisée fait référence à des assemblys d’interopérabilité SSIS comme Microsoft.SqlServer.DTSPipelineWrap ou Microsoft.SqlServer.DTSRuntimeWrap, définissez la valeur de la **incorporer les Types Interop** propriété ** False ».

![Incorporer les Types Interop](../../integration-services/extending-packages-custom-objects/media/embed-interop-types.png)

### <a name="unable-to-load-some-types-when-target-version-is-sql-server-2012"></a>Impossible de charger des types lors de la version cible est SQL Server 2012

Ce problème affecte certains types comme IErrorReportingService ou IUserPromptService.

**Message d’erreur (par exemple).** Impossible de charger le type 'Microsoft.DataWarehouse.Design.IErrorReportingService' de l’assembly ' Microsoft.DataWarehouse, Version = 13.0.0.0, Culture = neutral, PublicKeyToken = 89845dcd8080cc91'.

**Solution de contournement.** Utilisez un MessageBox au lieu de ces interfaces lorsque la version cible est SQL Server 2012.


