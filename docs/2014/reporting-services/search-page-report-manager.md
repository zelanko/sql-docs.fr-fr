---
title: Page de recherche (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 51ffdc07-e1b9-4ed7-acb3-dd98d7cce273
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 12413c103230d8c085a9701e3fb83db15135895a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66102259"
---
# <a name="search-page-report-manager"></a>Page Rechercher (Gestionnaire de rapports)
  La page Résultats de la recherche vous permet d'afficher les résultats d'une recherche spécifiée pour un rapport, un rapport lié, un modèle de rapport, une source de données partagée, un dossier ou une ressource. Les résultats de la recherche sont répertoriés par ordre alphabétique. Vous pouvez les trier par type, nom ou description.  
  
 Les éléments suivants sont exclus d'une recherche : instantanés de rapport contenus dans l'historique de rapport, abonnements et planifications partagées. De la même façon, une autorisation insuffisante pour afficher un dossier ou un rapport exclut cet élément de la recherche.  
  
 Vous ne pouvez pas rechercher du texte dans un rapport ou modèle. Pour rechercher un texte spécifique dans un rapport, utilisez la barre d'outils située dans la partie supérieure du rapport.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-search-results-page"></a>Pour ouvrir la page Résultats de la recherche  
  
1.  Ouvrez le Gestionnaire de rapports.  
  
2.  En haut de la page, tapez vos critères de recherche dans la zone de **recherche**. Appuyez ensuite sur ENTRÉE ou cliquez sur la flèche Rechercher.  
  
## <a name="options"></a>Options  
 **Supprimer**  
 Cliquez pour supprimer un élément d'une base de données du serveur de rapports.  
  
> [!NOTE]  
>  Ce bouton est uniquement disponible dans **Mode Détails**. Toutefois, vous pouvez pointer sur un élément et utiliser le menu pour accéder aux fonctionnalités de suppression dans **Mode Détails** ou **Mode Liste**.  
  
 **Déplacer**  
 Cliquez pour déplacer un élément. Vous ouvrez ainsi la page Déplacer les éléments dans laquelle vous pouvez sélectionner un autre emplacement de dossier.  
  
> [!NOTE]  
>  Ce bouton est uniquement disponible dans **Mode Détails**. Toutefois, vous pouvez pointer sur un élément et utiliser le menu pour accéder aux fonctionnalités de déplacement dans **Mode Détails** ou **Mode Liste**.  
  
 Zone de recherche  
 Tapez une partie ou l'intégralité du nom de l'élément que vous recherchez, puis cliquez sur **Atteindre** pour démarrer la recherche. La chaîne la plus longue que vous pouvez rechercher ne peut pas excéder 128 caractères.  
  
 Les noms d'éléments ou les descriptions qui contiennent toute la chaîne de recherche n'importe où dans le texte sont inclus dans les résultats de la recherche.  
  
 Les opérateurs booléens tels que le caractère plus (+) ne sont pas pris en charge.  
  
 **Mode Détails**  
 Cliquez pour afficher la page Résultats de la recherche dans une liste qui contient des informations supplémentaires sur les éléments, tels que le type d'élément, le nom, la description, le dossier dans lequel l'élément se trouve, et la date de sa dernière exécution. En **Mode Détails**, vous pouvez utiliser les boutons **Supprimer** et **Déplacer** pour supprimer et déplacer des éléments dans le dossier.  
  
 Pointez sur un élément et cliquez sur la flèche déroulante pour ouvrir le menu déroulant à partir duquel vous pouvez accéder aux propriétés de l'élément sélectionné et les configurer.  
  
 **Mode liste**  
 Cliquez pour afficher la page Résultats de la recherche sans détails comme dans **Mode Détails**. Mode Liste est la vue par défaut lorsque la page Résultats de la recherche s'ouvre.  
  
 Pointez sur un élément et cliquez sur la flèche déroulante pour ouvrir le menu déroulant à partir duquel vous pouvez accéder aux propriétés de l'élément sélectionné et les configurer.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Aide F1 du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
