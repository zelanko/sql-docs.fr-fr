---
title: Mapper des paramètres de requête à des variables dans un composant de flux de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 5e26977c-758c-46d6-acf1-4fd9238f0950
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 4a1d86dce6be4ed342fe8d90fefe53649533b816
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84915239"
---
# <a name="map-query-parameters-to-variables-in-a-data-flow-component"></a>Mapper des paramètres de requête à des variables dans un composant de flux de données
  Lorsque vous configurez la source OLE DB pour utiliser des requêtes paramétrables, vous pouvez mapper les paramètres à des variables.  
  
 La source OLE DB utilise des requêtes paramétrables pour filtrer les données lorsqu'elle se connecte à une source de données.  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a>Pour mapper un paramètre de requête à une variable  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de données** , puis dans la **Boîte à outils**, faites glisser la source OLE DB sur l'aire de conception.  
  
4.  Cliquez avec le bouton droit sur la source OLE DB, puis cliquez sur **Modifier**.  
  
5.  Dans l' **Éditeur de source OLE DB**, choisissez un gestionnaire de connexions OLE DB à utiliser pour se connecter à la source de données ou cliquez sur **Nouveau** pour créer un gestionnaire de connexions OLE DB.  
  
6.  Sélectionnez l'option **Commande SQL** comme mode d'accès aux données, puis tapez une requête paramétrable dans le volet **Texte de la commande SQL** .  
  
7.  Cliquez sur **Paramètres**.  
  
8.  Dans la boîte de dialogue **définir les paramètres** de la requête, mappez chaque paramètre de la liste **paramètres** à une variable de la liste **variables** ou créez une variable en cliquant sur **\<New variable>** . Cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Seules les variables système et les variables définies par l'utilisateur qui se trouvent dans l'étendue du package, dans un conteneur parent tel qu'une boucle Foreach ou dans la tâche de flux de données contenant le composant de flux de données, peuvent être mappées. La variable doit avoir un type de données compatible avec la colonne de la clause WHERE à laquelle le paramètre est affecté.  
  
9. Vous pouvez cliquer sur **Aperçu** pour afficher jusqu'à 200 lignes de données renvoyées par la requête.  
  
10. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Source OLE DB](ole-db-source.md)   
 [Transformation de recherche](transformations/lookup-transformation.md)  
  
  
