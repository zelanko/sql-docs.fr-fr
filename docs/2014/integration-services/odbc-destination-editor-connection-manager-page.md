---
title: Éditeur de Destination ODBC (Page Gestionnaire de connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.connection.f1
ms.assetid: f6d9c6c2-e4c4-468b-9e0d-af7b9609614d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bc651d10df7433bdb0217414f251d16ed6abdf70
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58390867"
---
# <a name="odbc-destination-editor-connection-manager-page"></a>Éditeur de destination ODBC (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de destination ODBC** pour sélectionner le gestionnaire de connexions ODBC de la destination. Cette page vous permet également de sélectionner une table ou une vue à partir de la base de données.  
  
 Pour plus d'informations sur cette destination ODBC, consultez [ODBC Destination](data-flow/odbc-destination.md).  
  
 **Pour ouvrir l'Éditeur de destination ODBC (page Gestionnaire de connexions)**  
  
## <a name="task-list"></a>Liste des tâches  
  
-   Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] qui possède la destination ODBC.  
  
-   Sous l’onglet **Flux de données** , double-cliquez sur la destination ODBC.  
  
-   Dans l' **Éditeur de destination ODBC**, cliquez sur **Gestionnaire de connexions**.  
  
## <a name="options"></a>Options  
  
### <a name="connection-manager"></a>Gestionnaire de connexions  
 Sélectionnez un gestionnaire de connexions ODBC existant dans la liste ou cliquez sur Nouveau pour créer une nouvelle connexion. La connexion peut concerner n'importe quelle base de données prise en charge par ODBC.  
  
### <a name="new"></a>Nouvelle  
 Cliquez sur **Nouveau**. La boîte de dialogue **Configurer l'Éditeur du gestionnaire de connexions ODBC** s'ouvre et vous permet de créer un nouveau gestionnaire de connexions.  
  
### <a name="data-access-mode"></a>Mode d'accès aux données  
 Spécifiez la méthode de chargement des données dans la destination. Ces fonctions sont répertoriées dans le tableau suivant :  
  
|Option|Description|  
|------------|-----------------|  
|Nom de la table - Lot|Sélectionnez cette option pour configurer la destination ODBC en mode par lot. Lorsque vous sélectionnez cette option, les options suivantes sont disponibles :|  
||**Nom de la table ou la vue**: Sélectionnez une table disponible ou une vue dans la liste.<br /><br /> Cette liste contient les 1 000 premières tables uniquement. Si votre base de données contient plus de 1000 tables, vous pouvez taper le début du nom d’une table ou utiliser le caractère générique (\*) pour entrer une partie du nom afin d’afficher la table ou les tables que vous souhaitez utiliser.<br /><br /> **Taille de lot**: Tapez la taille du lot pour le chargement en masse. Il s'agit du nombre de lignes chargées dans un même lot.|  
|Nom de la table - Ligne par ligne|Sélectionnez cette option pour configurer la destination ODBC de manière à insérer les lignes dans la table de destination une par une. Lorsque vous sélectionnez cette option, l'option suivante est disponible :|  
||**Nom de la table ou la vue**: Sélectionnez une table disponible ou une vue à partir de la base de données à partir de la liste.<br /><br /> Cette liste contient les 1 000 premières tables uniquement. Si votre base de données contient plus de 1 000 tables, vous pouvez taper le début du nom d'une table ou utiliser le caractère générique (*) pour entrer une partie du nom afin d'afficher la table ou les tables que vous souhaitez utiliser.|  
  
### <a name="preview"></a>Preview  
 Cliquez sur **Aperçu** pour afficher jusqu'à 200 lignes de données pour la table sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés personnalisées des destinations ODBC](data-flow/odbc-destination-custom-properties.md)   
 [Éditeur de destination ODBC &#40;page Mappages&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md)   
 [Éditeur de destination ODBC &#40;page Sortie d’erreur&#41;](../../2014/integration-services/odbc-destination-editor-error-output-page.md)  
  
  
