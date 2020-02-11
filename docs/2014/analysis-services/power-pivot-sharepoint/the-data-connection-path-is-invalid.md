---
title: "Le chemin d'accès à la connexion de données dans le classeur pointe vers un fichier sur le lecteur local, ou est un URI non valide. Échec de l’actualisation des connexions suivantes : données PowerPivot | Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0cc18a2c7111c71b62f77f5f52727a4a50a661ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66071037"
---
# <a name="the-data-connection-path-in-the-workbook-points-to-a-file-on-the-local-drive-or-is-an-invalid-uri-the-following-connections-failed-to-refresh-powerpivot-data"></a>Le chemin d'accès à la connexion de données dans le classeur pointe vers un fichier sur le lecteur local, ou est un URI non valide. Échec de l'actualisation des connexions suivantes : Données PowerPivot
  Pour les classeurs Excel contenant les données PowerPivot, Excel Services retourne cette erreur s'il ne peut pas se connecter aux sources de données incorporées.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S’applique à|PowerPivot pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause :|Excel Services est configuré pour autoriser uniquement les connexions de données à partir de fichiers .odc se trouvant dans une bibliothèque de connexions de données approuvées.|  
|Texte du message|Le chemin d'accès à la connexion de données dans le classeur pointe vers un fichier sur le lecteur local, ou est un URI non valide. Échec de l'actualisation des connexions suivantes : Données PowerPivot|  
  
## <a name="explanation"></a>Explication  
 Les classeurs PowerPivot contiennent des connexions de données incorporées. Pour prendre en charge l'interaction de classeurs via des segments et des filtres, Excel Services doit être configuré pour autoriser l'accès aux données externes via des informations de connexion incorporées. L'accès aux données externes est requis pour la récupération de données PowerPivot chargées sur des serveurs PowerPivot de la batterie de serveurs.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Modifiez les paramètres de configuration pour autoriser les connections à une source de données incorporée.  
  
1.  Dans administration centrale, dans gestion des applications, cliquez sur **gérer les applications de service**.  
  
2.  Cliquez sur **Application Excel Services**.  
  
3.  Cliquez sur **Emplacement de fichier approuvé**.  
  
4.  Cliquez sur **http://** ou sur l’emplacement à configurer.  
  
5.  Dans Données externes, dans Autoriser les données externes, cliquez sur **Bibliothèques de connexions de données approuvées et incorporées**.  
  
6.  Cliquez sur **OK**.  
  
 Vous pouvez également créer un emplacement approuvé pour les sites qui contiennent des classeurs PowerPivot, puis modifier les paramètres de configuration uniquement pour ce site. Pour plus d'informations, consultez [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
