---
title: Créer une Source de données incorporée ou partagée (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], creating
ms.assetid: b111a8d0-a60d-4c8b-b00a-51644b19c34b
caps.latest.revision: 40
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9cd820de9b6710e4524b39323bcc9837fad820b6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230729"
---
# <a name="create-an-embedded-or-shared-data-source-ssrs"></a>Créer une source de données incorporée ou partagée (SSRS)
  Une source de données de rapport spécifie un nom et des informations de connexion. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend deux types de sources de données en charge : incorporée et partagée. Une source de données incorporée est définie dans une définition de rapport et utilisée uniquement par ce rapport. Une source de données partagée est définie sous la forme d'un élément distinct et peut être utilisée par plusieurs rapports. Pour plus d’informations, consultez [incorporé et connexions de données partagées ou les Sources de données &#40;Générateur de rapports et SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md).  
  
 Dans le Générateur de rapports, vous accédez au serveur de rapports ou au site SharePoint et sélectionnez les sources de données ou créez des sources de données incorporées. Vous ne pouvez pas créer de sources de données partagées dans le Générateur de rapports.  
  
 Dans le Concepteur de rapports, vous pouvez créer des sources de données partagées ou incorporées. Dans le volet données du rapport, commencez à créer une référence de source de données, puis sélectionnez le **New** option. Après avoir créé une référence de source de données, une nouvelle source de données partagée est automatiquement ajoutée à l'Explorateur de solutions dans le dossier Sources de données partagées.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
 Vous pouvez également créer des sources de données partagées directement sur un serveur de rapports ou sur un site SharePoint. Pour plus d’informations, consultez [créer, supprimer ou modifier une Source de données partagée &#40;le Gestionnaire de rapports&#41; ](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) ou [créer et gérer des Sources de données partagées &#40;Reporting Services en Mode intégré SharePoint&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).  
  
### <a name="to-create-an-embedded-or-shared-data-source"></a>Pour créer une source de données incorporée ou partagée  
  
1.  Dans la barre d'outils du volet des données de rapport, cliquez sur **Nouveau** , puis sur **Source de données**. La boîte de dialogue **Propriétés de la source de données** s'ouvre.  
  
    > [!NOTE]  
    >  Si le volet des données de rapport n’est pas visible, cliquez sur l’option **Données du rapport** du menu **Affichage** .  
  
2.  Dans la zone de texte **Nom** , tapez un nom pour la source de données ou acceptez la valeur par défaut. Le nom de la source de données est utilisé en interne dans le rapport. Par souci de clarté, il est recommandé que le nom de la source de données contienne le nom de la base de données spécifiée dans la chaîne de connexion.  
  
3.  Pour une source de données incorporée, vérifiez que **connexion incorporée** est sélectionné.  
  
    1.  Dans la liste déroulante **Type** , sélectionnez un type de source de données ; par exemple, **Microsoft SQL Server** ou **OLE DB**.  
  
    2.  Spécifiez une chaîne de connexion à l'aide de l'une des méthodes suivantes :  
  
    -   Tapez directement la chaîne de connexion dans la zone de texte **Chaîne de connexion** . Pour obtenir la liste des exemples de chaînes de connexion, consultez [des connexions de données, les Sources de données et les chaînes de connexion dans le Générateur de rapports](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) ou [des connexions de données, les Sources de données et les chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
    -   Cliquez sur le bouton d’expression (**fx)** pour créer une expression qui prend la valeur d’une chaîne de connexion. Dans la boîte de dialogue **Expression** , tapez l'expression dans le volet Expression. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
    -   Cliquez sur **Modifier** pour ouvrir la boîte de dialogue **Propriétés de connexion** correspondant au type de source de données choisi à l'étape 2.  
  
         Renseignez les champs de la boîte de dialogue **Propriétés de connexion** comme il convient pour le type de source de données. Les propriétés de connexion incluent le type de la source de données, son nom, ainsi que les informations d'identification à utiliser. Une fois que vous avez spécifié les valeurs dans cette boîte de dialogue, cliquez sur **Tester la connexion** pour vérifier que la source de données est disponible et que les informations d'identification indiquées sont correctes. Pour plus d’informations sur les types de source de données spécifiques, consultez les rubriques dans [Ajouter des données à partir de sources de données externes &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md).  
  
4.  Pour une source de données partagée, vérifiez que **utiliser une référence de source de données partagée** est sélectionné.  
  
    1.  Cliquez sur **Nouveau**. Dans la boîte de dialogue de propriétés **Source de données partagée** , suivez les étapes 2 et 3 pour créer une source de données.  
  
    2.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
         La nouvelle source de données partagée apparaît dans le dossier Sources de données partagées, dans l'Explorateur de solutions.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     La source de données apparaît dans le volet des données de rapport. Dans ce volet, une source de données partagée pointe vers la définition de la source de données. Dans le Générateur de rapports, la définition de la source de données se trouve sur un serveur de rapports ou sur un site SharePoint. Dans le Concepteur de rapports, la définition de la source de données est un fichier qui se trouve dans l'Explorateur de solutions, dans le dossier Sources de données partagées.  
  
### <a name="to-import-an-existing-data-source-in-report-designer"></a>Pour importer une source de données existante dans le Concepteur de rapports  
  
1.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le dossier **Sources de données partagées** dans le projet Report Server, puis cliquez sur **Ajouter un élément existant**. La boîte de dialogue **Ajouter un élément existant** s'ouvre.  
  
2.  Accédez à un fichier de source de données partagée (rds) de définition de rapport existant, puis cliquez sur **Ouvrir**.  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-convert-an-embedded-data-source-to-a-shared-data-source-in-report-designer"></a>Pour convertir une source de données partagée en source de données incorporée dans le Concepteur de rapports  
  
-   Dans le volet données du rapport, avec le bouton droit de la source de données, puis sélectionnez **convertir en Source de données partagée**.  
  
### <a name="to-convert-a-shared-data-source-to-an-embedded-data-source-in-report-builder"></a>Pour convertir une source de données partagée en source de données incorporée dans le Générateur de rapports  
  
-   Dans le volet données du rapport, avec le bouton droit de la source de données et ouvrez **propriétés Source de données**.  
  
-   Cliquez sur **connexion incorporée** et terminer la création de la source de données incorporées comme décrit précédemment.  
  
## <a name="see-also"></a>Voir aussi  
 [Stocker des informations d’identification dans une source de données Reporting Services](report-data/store-credentials-in-a-reporting-services-data-source.md)   
 [Incorporée et partagée des connexions de données ou Sources de données &#40;Générateur de rapports et SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [Convertir à partir d’une Source de données incorporée en source partagée &#40;Générateur de rapports et SSRS&#41;](report-data/convert-data-sources-report-builder-and-ssrs.md)   
 [Lier un rapport ou un modèle à une Source de données partagée &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md)   
 [Configurer les propriétés de la source de données d’un rapport &#40;Gestionnaire de rapports&#41;](report-data/configure-data-source-properties-for-a-report-report-manager.md)   
 [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
