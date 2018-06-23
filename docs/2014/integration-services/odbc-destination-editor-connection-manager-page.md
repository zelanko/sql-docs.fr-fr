---
title: Éditeur de Destination ODBC (Page Gestionnaire de connexions) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.designer.odbcdest.connection.f1
ms.assetid: f6d9c6c2-e4c4-468b-9e0d-af7b9609614d
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ce1766615afb37976cc92c66c99de173ed3e9364
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044986"
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
||**Nom de la table ou de la vue**: sélectionnez une table ou une vue disponible dans la liste.<br /><br /> Cette liste contient les 1 000 premières tables uniquement. Si votre base de données contient plus de 1000 tables, vous pouvez taper le début du nom d’une table ou utiliser le caractère générique (\*) pour entrer une partie du nom afin d’afficher la table ou les tables que vous souhaitez utiliser.<br /><br /> **Taille du lot**: entrez la taille du lot pour le chargement en bloc. Il s'agit du nombre de lignes chargées dans un même lot.|  
|Nom de la table - Ligne par ligne|Sélectionnez cette option pour configurer la destination ODBC de manière à insérer les lignes dans la table de destination une par une. Lorsque vous sélectionnez cette option, l'option suivante est disponible :|  
||**Nom de la table ou de la vue**: sélectionnez dans la liste une table ou une vue disponible dans la base de données.<br /><br /> Cette liste contient les 1 000 premières tables uniquement. Si votre base de données contient plus de 1 000 tables, vous pouvez taper le début du nom d'une table ou utiliser le caractère générique (*) pour entrer une partie du nom afin d'afficher la table ou les tables que vous souhaitez utiliser.|  
  
### <a name="preview"></a>Aperçu  
 Cliquez sur **Aperçu** pour afficher jusqu'à 200 lignes de données pour la table sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés personnalisées des destinations ODBC](data-flow/odbc-destination-custom-properties.md)   
 [Éditeur de destination ODBC &#40;page Mappages&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md)   
 [Éditeur de Destination ODBC &#40;Page sortie d’erreur&#41;](../../2014/integration-services/odbc-destination-editor-error-output-page.md)  
  
  