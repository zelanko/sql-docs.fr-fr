---
title: Destination ODBC | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.f1
ms.assetid: bffa63e0-c737-4b54-b4ea-495a400ffcf8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9de91ba98533e82fbf63376ed6d9c56ad73a000c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62771025"
---
# <a name="odbc-destination"></a>Destination ODBC
  La destination ODBC charge en masse les données dans les tables de base de données compatibles ODBC. La destination ODBC utilise un gestionnaire de connexions ODBC pour se connecter à la source de données.  
  
 Une destination ODBC inclut des mappages entre les colonnes d'entrée et les colonnes de la source de données de destination. Vous n’avez pas besoin de mapper les colonnes d’entrée à toutes les colonnes de destination, mais en fonction des propriétés des colonnes de destination, des erreurs peuvent se produire si aucune colonne d’entrée n’est mappée aux colonnes de destination. Par exemple, si une colonne de destination n'autorise pas les valeurs null, une colonne d'entrée doit être mappée à cette colonne. En outre, même si des colonnes de types différents peuvent être mappées, si les données d'entrée ne sont pas compatibles pour le type de colonne de destination, une erreur se produit au moment de l'exécution. En fonction du comportement des erreurs configuré, l'erreur sera ignorée, entraînera un échec ou la ligne sera envoyée à la sortie d'erreur.  
  
 La destination ODBC comporte une sortie standard et une sortie d'erreur.  
  
##  <a name="load-options"></a><a name="BKMK_odbcdestination_loadoptions"></a> Options de chargement  
 La destination ODBC peut utiliser l'un des deux modules de charge d'accès. Vous définissez le mode dans l’[Éditeur de source ODBC &#40;page Gestionnaire de connexions&#41;](../odbc-source-editor-connection-manager-page.md). Les deux modes sont :  
  
-   **Lot**: dans ce mode, la destination ODBC tente d’utiliser la méthode d’insertion la plus efficace en fonction des capacités perçues du fournisseur ODBC. Pour la plupart des fournisseurs modernes ODBC, cela implique de préparer une instruction INSERT avec des paramètres, puis d’utiliser une liaison de paramètre de table selon les lignes (où la taille de la table est contrôlée par la propriété **BatchSize** ). Si vous sélectionnez **Lot** et que le fournisseur ne prend pas en charge cette méthode, la destination ODBC bascule automatiquement en mode **Ligne par ligne** .  
  
-   **Ligne par ligne**: dans ce mode, la destination ODBC prépare une instruction INSERT avec des paramètres et utilise **SQL Execute** pour insérer les lignes une par une.  
  
## <a name="error-handling"></a>Gestion des erreurs  
 La destination ODBC a une sortie d'erreur. La sortie d'erreur du composant contient les colonnes de sortie suivantes :  
  
-   **Code d’erreur**: numéro qui correspond à l’erreur actuelle. Consultez la documentation de votre base de données source pour obtenir la liste des erreurs. Pour obtenir la liste des codes d'erreur SSIS, consultez le Guide de référence des erreurs et des événements SSIS.  
  
-   **Colonne d’erreur**: colonne source à l’origine de l’erreur (pour les erreurs de conversion).  
  
-   Colonnes de données de sortie standard.  
  
 Selon le comportement paramétré pour les erreurs, la destination ODBC prend en charge les erreurs de retour (conversion de données, troncation) qui se produisent pendant le processus de récupération dans la sortie d'erreur. Pour plus d’informations, consultez [Éditeur de source ODBC &#40;page Sortie d’erreur&#41;](../odbc-source-editor-error-output-page.md).  
  
## <a name="parallelism"></a>Parallélisme  
 Il n'existe aucune limitation quant au nombre de composants de destination ODBC pouvant s'exécuter en parallèle sur la même table ou des tables différentes, sur le même ordinateur ou sur des ordinateurs différents (autre que les limites de session globale habituelles).  
  
 Toutefois, les limites du fournisseur ODBC utilisé peuvent limiter le nombre de connexions simultanées par le fournisseur. Ces limites restreignent le nombre d'instances parallèles prises en charge pour la destination ODBC. Le développeur SSIS doit avoir connaissance des limites de tout fournisseur ODBC utilisé et en tenir compte lors de la génération de packages SSIS.  
  
 Vous devez également savoir qu'un chargement simultané dans la même table peut réduire les performances en raison du verrouillage des enregistrements standard. Cela dépend des données chargées et de l'organisation de table.  
  
## <a name="troubleshooting-the-odbc-destination"></a>Résolution des problèmes liés à la destination ODBC  
 Vous pouvez consigner dans un journal les appels que la source ODBC effectue vers des fournisseurs de données externes. Cette fonctionnalité de journalisation permet de résoudre des problèmes liés à l'enregistrement de données vers des sources de données externes que réalise la destination ODBC. Pour consigner les appels effectués par la destination ODBC vers des fournisseurs ODBC externes, activez la trace du gestionnaire de pilotes ODBC. Pour plus d’informations, consultez la documentation Microsoft sur la *génération d’une trace ODBC avec l’administrateur de sources de données ODBC*.  
  
## <a name="configuring-the-odbc-destination"></a>Configuration de la destination ODBC  
 Vous pouvez configurer la destination ODBC par programmation ou par le biais du concepteur SSIS  
  
 Pour plus d’informations, consultez l’une des rubriques suivantes :  
  
-   [Éditeur de destination ODBC &#40;page Gestionnaire de connexions&#41;](../odbc-destination-editor-connection-manager-page.md)  
  
-   [Éditeur de destination ODBC &#40;page Mappages&#41;](../odbc-destination-editor-mappings-page.md)  
  
-   [Éditeur de destination ODBC &#40;page Sortie d’erreur&#41;](../odbc-destination-editor-error-output-page.md)  
  
 La boîte de dialogue **Éditeur avancé** contient les propriétés qui peuvent être définies par programme.  
  
 Pour ouvrir la boîte de dialogue **Éditeur avancé** :  
  
-   Sur l’écran **Flux de données** de votre projet [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] , cliquez avec le bouton droit sur la destination ODBC, puis sélectionnez **Afficher l’éditeur avancé**.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue Éditeur avancé, consultez [Propriétés personnalisées des destinations ODBC](odbc-destination-custom-properties.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Éditeur de destination ODBC &#40;page Sortie d’erreur&#41;](../odbc-destination-editor-error-output-page.md)  
  
-   [Éditeur de destination ODBC &#40;page Mappages&#41;](../odbc-destination-editor-mappings-page.md)  
  
-   [Éditeur de destination ODBC &#40;page Gestionnaire de connexions&#41;](../odbc-destination-editor-connection-manager-page.md)  
  
-   [Charger des données à l'aide de la destination ODBC](odbc-destination.md)  
  
-   [Propriétés personnalisées des destinations ODBC](odbc-destination-custom-properties.md)  
  
  
