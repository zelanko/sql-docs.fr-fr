---
title: "Le chemin d'accès à la connexion de données dans le classeur pointe vers un fichier sur le lecteur local, ou est un URI non valide. Impossible d’actualiser les connexions suivantes : données PowerPivot | Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6242e258c8516b4ebd6e46e9290dabe31cbaf168
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164119"
---
# <a name="the-data-connection-path-in-the-workbook-points-to-a-file-on-the-local-drive-or-is-an-invalid-uri-the-following-connections-failed-to-refresh-powerpivot-data"></a>Le chemin d'accès à la connexion de données dans le classeur pointe vers un fichier sur le lecteur local, ou est un URI non valide. Échec de l'actualisation des connexions suivantes : Données PowerPivot
  Pour les classeurs Excel contenant les données PowerPivot, Excel Services retourne cette erreur s'il ne peut pas se connecter aux sources de données incorporées.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S'applique à|PowerPivot pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|Excel Services est configuré pour autoriser uniquement les connexions de données à partir de fichiers .odc se trouvant dans une bibliothèque de connexions de données approuvées.|  
|Texte du message|Le chemin d'accès à la connexion de données dans le classeur pointe vers un fichier sur le lecteur local, ou est un URI non valide. Échec de l'actualisation des connexions suivantes : Données PowerPivot|  
  
## <a name="explanation"></a>Explication  
 Les classeurs PowerPivot contiennent des connexions de données incorporées. Pour prendre en charge l'interaction de classeurs via des segments et des filtres, Excel Services doit être configuré pour autoriser l'accès aux données externes via des informations de connexion incorporées. L'accès aux données externes est requis pour la récupération de données PowerPivot chargées sur des serveurs PowerPivot de la batterie de serveurs.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Modifiez les paramètres de configuration pour autoriser les connections à une source de données incorporée.  
  
1.  Dans l'Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur **Application Excel Services**.  
  
3.  Cliquez sur **Emplacement de fichier approuvé**.  
  
4.  Cliquez sur **http://** ou sur l’emplacement à configurer.  
  
5.  Dans Données externes, dans Autoriser les données externes, cliquez sur **Bibliothèques de connexions de données approuvées et incorporées**.  
  
6.  Cliquez sur **OK**.  
  
 Vous pouvez également créer un emplacement approuvé pour les sites qui contiennent des classeurs PowerPivot, puis modifier les paramètres de configuration uniquement pour ce site. Pour plus d'informations, consultez [Créer un emplacement approuvé pour les sites PowerPivot dans l'Administration centrale](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
