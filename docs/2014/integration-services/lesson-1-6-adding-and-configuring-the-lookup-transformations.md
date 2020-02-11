---
title: 'Étape 6 : Ajout et configuration des transformations de recherche | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5c59f723-9707-4407-80ae-f05f483cf65f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f652519efc4b77bd785cdded468fe114f6499200
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62891547"
---
# <a name="step-6-adding-and-configuring-the-lookup-transformations"></a>Étape 6 : Ajout et configuration des transformations de recherche
  Une fois que vous avez configuré la source de fichier plat pour extraire les données du fichier source, la tâche suivante consiste à définir les transformations de recherche nécessaires pour obtenir les valeurs de **CurrencyKey** et **DateKey**. Une transformation de recherche effectue une recherche en joignant les données dans la colonne d'entrée spécifiée à une colonne dans un dataset de référence. Le dataset de référence peut être une table ou une vue existante, une nouvelle table ou le résultat d'une instruction SQL. Dans ce didacticiel, la transformation de recherche utilise un gestionnaire de connexions OLE DB pour se connecter à la base de données qui contient les données servant de source au jeu de données de référence.  
  
> [!NOTE]  
>  Vous pouvez également configurer la transformation de recherche afin qu'elle se connecte à un cache qui contient le jeu de données de référence. Pour plus d’informations, consultez [Lookup transformation](data-flow/transformations/lookup-transformation.md).  
  
 Dans le cadre de ce didacticiel, vous allez ajouter et configurer les deux composants de transformation de recherche suivants dans le package :  
  
-   Une transformation pour effectuer une recherche des valeurs à partir de la colonne **CurrencyKey** de la table de dimensions **DimCurrency** basée sur la correspondance avec les valeurs de la colonne **CurrencyID** à partir du fichier plat.  
  
-   Une transformation pour effectuer une recherche des valeurs à partir de la colonne **DateKey** de la table de dimensions **DimDate** basée sur la correspondance avec les valeurs de la colonne **CurrencyDate** à partir du fichier plat.  
  
 Dans les deux cas, la transformation de recherche utilise le Gestionnaire de connexions OLE DB que vous avez créé précédemment.  
  
### <a name="to-add-and-configure-the-lookup-currency-key-transformation"></a>Pour ajouter et configurer la transformation Lookup Currency Key  
  
1.  Dans la **boîte à outils SSIS**, développez **commun**, puis faites glisser **recherche** sur l’aire de conception de l’onglet de **Workflow** . Placez la recherche directement sous la source de **données extraire l’exemple de devise** .  
  
2.  Sélectionnez la source de fichier plat **Extract Sample Currency Data** et faites glisser la flèche verte vers la transformation de **recherche** que vous venez d'ajouter pour connecter les deux composants.  
  
3.  Dans l'aire de conception **Flux de données** , cliquez sur **Recherche** dans la transformation de **Recherche** , puis remplacez le nom par **Lookup Currency Key**.  
  
4.  Double-cliquez sur la transformation **Lookup CurrencyKey** pour afficher l’éditeur de transformation de recherche.  
  
5.  Dans la page **Général** , effectuez les sélections suivantes :  
  
    1.  Sélectionnez **Cache complet**.  
  
    2.  Dans la zone **Type de connexion** , sélectionnez **Gestionnaire de connexions OLE DB**.  
  
6.  Dans la page **Connexion** , effectuez les sélections suivantes :  
  
    1.  Dans la boîte de dialogue **Gestionnaire de connexions OLE DB** , assurez-vous que **localhost.AdventureWorksDW2012** est affiché.  
  
    2.  Sélectionnez **Utiliser les résultats d'une requête SQL**, puis tapez ou copiez l'instruction SQL suivante :  
  
        ```  
        select * from (select * from [dbo].[DimCurrency]) as refTable  
        where [refTable].[CurrencyAlternateKey] = 'ARS'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'AUD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'BRL'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CAD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CNY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'DEM'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'EUR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'FRF'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'GBP'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'JPY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'MXN'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'SAR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'USD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'VEB'  
        ```  
  
7.  Dans la page **Colonnes** , effectuez les sélections suivantes :  
  
    1.  Dans le volet **Colonnes d'entrée disponibles** , faites glisser **CurrencyID** vers le volet **Colonnes de recherche disponibles** et déposez cet élément sur **CurrencyAlternateKey**.  
  
    2.  Dans la liste **Colonnes de recherche disponibles** , activez la case à cocher située à gauche de **CurrencyKey**.  
  
8.  Cliquez sur **OK** pour revenir à l'aire de conception **Flux de données** .  
  
9. Double-cliquez sur la transformation Lookup Currency Key, puis cliquez sur **Propriétés**.  
  
10. Dans la Fenêtre Propriétés, vérifiez que la `LocaleID` propriété est définie sur **anglais (États-Unis)** et que la propriété **DefaultCodePage** est définie sur **1252**.  
  
### <a name="to-add-and-configure-the--lookup-datekey-transformation"></a>Pour ajouter et configurer la transformation Lookup Date Key  
  
1.  Dans la **Boîte à outils SSIS**, faites glisser **Recherche** vers l'aire de conception **Flux de données** . Placez la recherche directement sous la transformation **Lookup Currency Key** .  
  
2.  Sélectionnez la transformation **Lookup Currency Key** et faites glisser la flèche verte vers la transformation de **recherche** que vous venez d'ajouter pour connecter les deux composants.  
  
3.  Dans la boîte de dialogue **Sélection entrée et sortie** , cliquez sur **Sortie de recherche avec correspondance** dans la zone de liste de **Sortie** , puis cliquez sur **OK**.  
  
4.  Dans l'aire de conception **Flux de données** , cliquez sur **Recherche** dans la transformation **Recherche** que vous venez d'ajouter, puis remplacez le nom par **Lookup Date Key**.  
  
5.  Double-cliquez sur la transformation **Lookup Date Key** .  
  
6.  Dans la page **Général** , sélectionnez **Cache partiel**.  
  
7.  Dans la page **Connexion** , effectuez les sélections suivantes :  
  
    1.  Dans la boîte de dialogue **Gestionnaire de connexions OLE DB** , vérifiez que **localhost.AdventureWorksDW2012** est affiché.  
  
    2.  Dans la zone **Utiliser une table ou une vue** , tapez ou sélectionnez **[dbo].[DimDate]**.  
  
8.  Dans la page **Colonnes** , effectuez les sélections suivantes :  
  
    1.  Dans le volet **Colonnes d'entrée disponibles** , faites glisser **CurrencyDate** vers le volet **Colonnes de recherche disponibles** et déposez cet élément sur **FullDateAlternateKey**.  
  
    2.  Dans la liste **Colonnes de recherche disponibles** , activez la case à cocher située à gauche de **DateKey**.  
  
9. Dans la page **Avancé** , examinez les options de mise en cache.  
  
10. Cliquez sur **OK** pour revenir à l'aire de conception **Flux de données** .  
  
11. Double-cliquez sur la transformation Lookup Date Key, puis cliquez sur **Propriétés**.  
  
12. Dans la Fenêtre Propriétés, vérifiez que la `LocaleID` propriété est définie sur **anglais (États-Unis)** et que la propriété **DefaultCodePage** est définie sur **1252**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 7 : ajout et configuration de la destination OLE DB](lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation de recherche](data-flow/transformations/lookup-transformation.md)  
  
  
