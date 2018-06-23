---
title: "L'emplacement approuvé dans lequel le classeur est stocké n'autorise pas les connexions de données externes. Impossible d’actualiser les connexions suivantes : données PowerPivot | Documents Microsoft"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc0cedfd-a7d0-40ef-bdd6-ea508130640a
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 449ac77f0eaff4a5d3550711b18ec57751460918
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039394"
---
# <a name="the-trusted-location-where-the-workbook-is-stored-does-not-allow-external-data-connections-the-following-connections-failed-to-refresh-powerpivot-data"></a>L'emplacement approuvé dans lequel le classeur est stocké n'autorise pas les connexions de données externes. Échec de l'actualisation des connexions suivantes : Données PowerPivot
  Pour les classeurs Excel contenant les données PowerPivot, Excel Services retourne cette erreur s'il ne peut pas se connecter aux sources de données incorporées.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S'applique à|PowerPivot pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|Excel Services est configuré pour refuser l'accès aux données externes.|  
|Texte du message|L'emplacement approuvé dans lequel le classeur est stocké n'autorise pas les connexions de données externes. Échec de l'actualisation des connexions suivantes : Données PowerPivot|  
  
## <a name="explanation"></a>Explication  
 Les classeurs PowerPivot contiennent des connexions de données incorporées. Pour prendre en charge l'interaction de classeurs via des segments et des filtres, Excel Services doit être configuré pour autoriser l'accès aux données externes via des informations de connexion incorporées. L'accès aux données externes est requis pour la récupération de données PowerPivot chargées sur des serveurs PowerPivot de la batterie de serveurs.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Modifiez les paramètres de configuration pour autoriser les sources de données incorporées.  
  
1.  Dans l'Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur **Application Excel Services**.  
  
3.  Cliquez sur **Emplacement de fichier approuvé**.  
  
4.  Cliquez sur **http://** ou sur l’emplacement à configurer.  
  
5.  Dans Données externes, dans Autoriser les données externes, cliquez sur **Bibliothèques de connexions de données approuvées et incorporées**.  
  
6.  Cliquez sur **OK**.  
  
 Vous pouvez également créer un emplacement approuvé pour les sites qui contiennent des classeurs PowerPivot, puis modifier les paramètres de configuration uniquement pour ce site. Pour plus d'informations, consultez [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  