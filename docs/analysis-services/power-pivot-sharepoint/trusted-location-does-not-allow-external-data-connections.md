---
title: "Approuvé d’emplacement n’autorise pas les connexions de données externes | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: dc0cedfd-a7d0-40ef-bdd6-ea508130640a
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 74571e33141442205621edd3465761770ea53fe4
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="trusted-location-does-not-allow-external-data-connections"></a>Emplacement approuvé n’autorise pas les connexions de données externes
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Pour les classeurs Excel qui contiennent des [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] données, Excel Services retourne cette erreur s’il ne peut pas se connecter aux sources de données incorporées.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S'applique à|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|Excel Services est configuré pour refuser l'accès aux données externes.|  
|Texte du message|L'emplacement approuvé dans lequel le classeur est stocké n'autorise pas les connexions de données externes. Échec de l’actualisation des connexions suivantes : Données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
  
## <a name="explanation"></a>Explication  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] contiennent des connexions de données incorporées. Pour prendre en charge l'interaction de classeurs via des segments et des filtres, Excel Services doit être configuré pour autoriser l'accès aux données externes via des informations de connexion incorporées. L’accès aux données externes est requis pour la récupération de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] chargées sur des serveurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de la batterie de serveurs.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Modifiez les paramètres de configuration pour autoriser les sources de données incorporées.  
  
1.  Dans l'Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur **Application Excel Services**.  
  
3.  Cliquez sur **Emplacement de fichier approuvé**.  
  
4.  Cliquez sur **http://** ou sur l’emplacement à configurer.  
  
5.  Dans Données externes, dans Autoriser les données externes, cliquez sur **Bibliothèques de connexions de données approuvées et incorporées**.  
  
6.  Cliquez sur **OK**.  
  
 Vous pouvez également créer un emplacement approuvé pour les sites qui contiennent des classeurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , puis modifier les paramètres de configuration uniquement pour ce site. Pour plus d’informations, voir [Create a trusted location for Power Pivot sites in Central Administration](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
