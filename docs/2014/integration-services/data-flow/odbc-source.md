---
title: Source ODBC | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.f1
ms.assetid: abcf34eb-9140-4100-82e6-b85bccd22abe
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 53633e4f963b9d816487721b79388b8236281010
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297059"
---
# <a name="odbc-source"></a>Source ODBC
  La source ODBC extrait les données d'une base de données compatible ODBC à l'aide d'une table de base de données, d'une vue ou d'une instruction SQL.  
  
 La source ODBC utilise les modes d'accès aux données suivants pour extraire les données :  
  
-   Une table ou une vue.  
  
-   Les résultats d'une instruction SQL.  
  
 La source utilise un gestionnaire de connexions ODBC qui spécifie le fournisseur à utiliser.  
  
 Une source ODBC inclut les colonnes de sortie de données sources. Lorsque les colonnes de sortie sont mappées dans la destination ODBC aux colonnes de destination, des erreurs peuvent se produire si aucune colonne de sortie n'est mappée aux colonnes de destination. Même si des colonnes de types différents peuvent être mappées, si les données de sortie ne sont pas compatibles pour la destination, une erreur se produit au moment de l'exécution. En fonction du comportement des erreurs, l'erreur sera ignorée, entraînera un échec ou la ligne sera envoyée à la sortie d'erreur.  
  
 La source ODBC a une sortie normale et une sortie d'erreur.  
  
## <a name="error-handling"></a>Gestion des erreurs  
 La source ODBC a une sortie d'erreur. La sortie d'erreur du composant contient les colonnes de sortie suivantes :  
  
-   **Code d’erreur**: numéro qui correspond à l’erreur actuelle. Consultez la documentation de la base de données ODBC que vous utilisez pour obtenir une liste d'erreurs. Pour obtenir la liste des codes d'erreur SSIS, consultez le Guide de référence des erreurs et des événements SSIS.  
  
-   **Colonne d’erreur**: colonne source à l’origine de l’erreur (pour les erreurs de conversion).  
  
-   Colonnes de données de sortie standard.  
  
 Selon le comportement paramétré pour les erreurs, la source ODBC prend en charge les erreurs de retour (conversion de données, troncation) qui se produisent pendant le processus d'extraction dans la sortie d'erreur. Pour plus d’informations, consultez [Éditeur de destination ODBC &#40;page Gestionnaire de connexions&#41;](../odbc-destination-editor-connection-manager-page.md).  
  
## <a name="data-type-support"></a>Prise en charge du type de données  
 Pour plus d'informations sur les types de données pris en charge par la source ODBC, consultez le Connecteur pour Open Database Connectivity (ODBC) d'Attunity.  
  
## <a name="extract-options"></a>Options d'extraction  
 La source ODBC s’exécute en mode **Lot** ou **Ligne par ligne** . Le mode utilisé est déterminé par la propriété **FetchMethod** . La liste suivante décrit les différents modes.  
  
-   **Lot**: les composants tentent d’utiliser la méthode de récupération la plus efficace en fonction des capacités perçues du fournisseur ODBC. Pour la plupart des fournisseurs ODBC modernes, il s’agit de SQLFetchScroll avec une liaison de table (où la taille de la table est déterminée par la propriété **BatchSize** ). Si vous sélectionnez **Lot** et que le fournisseur ne prend pas en charge cette méthode, la destination ODBC bascule automatiquement en mode **Ligne par ligne** .  
  
-   **Ligne par ligne**: le composant utilise SQLFetch pour extraire les lignes une par une.  
  
 Pour plus d’informations sur la propriété **FetchMethod** , consultez [Propriétés personnalisées des sources ODBC](odbc-source-custom-properties.md).  
  
## <a name="parallelism"></a>Parallelism  
 Il n'existe aucune limitation quant au nombre de composants de source ODBC pouvant s'exécuter en parallèle sur la même table ou des tables différentes, sur le même ordinateur ou sur des ordinateurs différents (autre que les limites de session globale habituelles).  
  
 Toutefois, les limites du fournisseur ODBC utilisé peuvent limiter le nombre de connexions simultanées par le fournisseur. Ces limites restreignent le nombre d'instances parallèles prises en charge pour la source ODBC. Le développeur SSIS doit avoir connaissance des limites de tout fournisseur ODBC utilisé et en tenir compte lors de la génération de packages SSIS.  
  
## <a name="troubleshooting-the-odbc-source"></a>Résolution des problèmes liés à la source ODBC  
 Vous pouvez consigner dans un journal les appels que la source ODBC effectue vers des fournisseurs de données externes. Cette fonctionnalité de journalisation permet de résoudre des problèmes liés au chargement de données qu'effectue la source ODBC à partir de sources de données externes. Pour consigner les appels effectués par la source ODBC à destination de fournisseurs de données externes, activez la trace du gestionnaire de pilotes ODBC. Pour plus d’informations, consultez la documentation Microsoft intitulée *Génération d’une trace ODBC avec l’administrateur des source de données ODBC*.  
  
## <a name="configuring-the-odbc-source"></a>Configuration de la source ODBC  
 Vous pouvez définir la source ODBC par programmation ou par le biais du concepteur SSIS.  
  
 Pour plus d’informations, consultez l’une des rubriques suivantes :  
  
-   [Éditeur de Source ODBC &#40;Page Gestionnaire de connexions&#41;](../odbc-source-editor-connection-manager-page.md)  
  
-   [Éditeur de Source ODBC &#40;Page colonnes&#41;](../odbc-source-editor-columns-page.md)  
  
-   [Éditeur de Source ODBC &#40;Page sortie d’erreur&#41;](../odbc-source-editor-error-output-page.md)  
  
 La boîte de dialogue **Éditeur avancé** contient les propriétés qui peuvent être définies par programme.  
  
 Pour ouvrir la boîte de dialogue **Éditeur avancé** :  
  
-   Sur l’écran **Flux de données** de votre projet [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] , cliquez avec le bouton droit sur la source ODBC, puis sélectionnez **Afficher l’éditeur avancé**.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue Éditeur avancé, consultez [Propriétés personnalisées des sources ODBC](odbc-source-custom-properties.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Éditeur de Source ODBC &#40;Page sortie d’erreur&#41;](../odbc-source-editor-error-output-page.md)  
  
-   [Éditeur de Source ODBC &#40;Page colonnes&#41;](../odbc-source-editor-columns-page.md)  
  
-   [Éditeur de Source ODBC &#40;Page Gestionnaire de connexions&#41;](../odbc-source-editor-connection-manager-page.md)  
  
-   [Extraire des données à l’aide de la source ODBC](odbc-source.md)  
  
-   [Propriétés personnalisées des sources ODBC](odbc-source-custom-properties.md)  
  
  
