---
title: Éditeur de Source ODBC (Page Gestionnaire de connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.connection.f1
ms.assetid: e2c8dc83-6394-4d6c-9232-97e94be72431
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: aaf49a9894e5b2f3f35687b8575c35b5f19ebe81
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58378587"
---
# <a name="odbc-source-editor-connection-manager-page"></a>Éditeur de source ODBC (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source ODBC** pour sélectionner le gestionnaire de connexions ODBC pour la source. Cette page vous permet également de sélectionner une table ou une vue à partir de la base de données.  
  
 Pour plus d'informations sur la source ODBC, consultez [ODBC Source](data-flow/odbc-source.md).  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour ouvrir l'Éditeur de source ODBC (page Gestionnaire de connexions)**  
  
-   Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] qui possède la source ODBC.  
  
-   Sous l’onglet **Flux de données** , double-cliquez sur la source ODBC.  
  
## <a name="options"></a>Options  
  
### <a name="connection-manager"></a>Gestionnaire de connexions  
 Sélectionnez un gestionnaire de connexions ODBC existant dans la liste ou cliquez sur **Nouveau** pour créer une nouvelle connexion. La connexion peut concerner n'importe quelle base de données prise en charge par ODBC.  
  
### <a name="new"></a>Nouvelle  
 Cliquez sur **Nouveau**. La boîte de dialogue **Configurer l'Éditeur du gestionnaire de connexions ODBC** s'ouvre et vous permet de créer un nouveau gestionnaire de connexions ODBC.  
  
### <a name="data-access-mode"></a>Mode d'accès aux données  
 Spécifiez la méthode de sélection des données dans la source. Ces fonctions sont répertoriées dans le tableau suivant :  
  
|Option|Description|  
|------------|-----------------|  
|Nom de la table|Permet de récupérer les données d'une table ou d'une vue dans la source de données ODBC. Lorsque vous sélectionnez cette option, sélectionnez une valeur parmi les suivantes dans la liste :|  
||**Nom de la table ou la vue**: Sélectionnez une table disponible ou une vue dans la liste ou tapez une expression régulière pour identifier la table.|  
||Cette liste contient les 1 000 premières tables uniquement. Si votre base de données contient plus de 1 000 tables, vous pouvez taper le début du nom d'une table ou utiliser le caractère générique (*) pour entrer une partie du nom afin d'afficher la table ou les tables que vous souhaitez utiliser.|  
|Commande SQL|Extrayez les données de la source de données ODBC à l'aide d'une requête SQL. Vous devez écrire la requête dans la syntaxe de la base de données source dans laquelle vous travaillez. Lorsque vous sélectionnez cette option, entrez une requête selon l'une des méthodes suivantes :|  
||Entrez le texte de la requête SQL dans le champ **Texte de la commande SQL** .|  
||Cliquez sur **Parcourir** pour charger la requête SQL à partir d'un fichier texte.|  
||Pour vérifier la syntaxe du texte de la requête, cliquez sur **Analyser** .|  
  
### <a name="preview"></a>Preview  
 Cliquez sur **Aperçu** pour afficher les 200 premières lignes de données extraites de la table ou de la vue sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés personnalisées des sources ODBC](data-flow/odbc-source-custom-properties.md)   
 [Éditeur de source ODBC &#40;page Colonnes&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md)   
 [Éditeur de source ODBC &#40;page Sortie d’erreur&#41;](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
