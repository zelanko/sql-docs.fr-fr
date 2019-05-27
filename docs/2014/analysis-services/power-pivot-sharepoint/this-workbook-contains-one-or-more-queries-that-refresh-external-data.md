---
title: Ce classeur contient une ou plusieurs requêtes qui actualisent les données externes. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 925821cba91a8a62076f0dcfa327453d035671d9
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66070970"
---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a>Ce classeur contient une ou plusieurs requêtes qui actualisent les données externes.
  Pour les classeurs Excel qui contiennent des données PowerPivot, Excel Services affiche cet avertissement lorsqu'il détecte des informations de connexion et vous demande d'activer ou de désactiver des requêtes pour ce classeur.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|PowerPivot pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|Excel Services est configuré pour avertir lors de l'actualisation des données.|  
|Texte du message|Ce classeur contient une ou plusieurs requêtes qui actualisent les données externes. Un utilisateur malveillant peut concevoir une requête pour accéder aux informations confidentielles et les distribuer à d'autres utilisateurs ou effectuer d'autres actions malfaisantes.<br /><br /> Si vous approuvez la source de ce classeur, cliquez sur Oui pour activer les requêtes à des données externes dans ce classeur. Si vous avez des doutes, cliquez sur Non afin que les modifications ne soient pas appliquées à votre classeur.<br /><br /> Souhaitez-vous activer des requêtes à des données externes dans ce classeur ?|  
  
## <a name="explanation"></a>Explication  
 Les classeurs PowerPivot contiennent des chaînes de connexion de données incorporées, utilisées par Excel pour communiquer avec un serveur PowerPivot externe qui charge et calcule les données. Lorsque l'option Avertir lors de l'actualisation des données est activée, Excel Services détecte cette chaîne de connexion et avertit l'utilisateur en conséquence.  
  
 Pour filtrer et découper les données PowerPivot dans le classeur, les requêtes doivent être activées. Assurez-vous que vous activez des requêtes uniquement pour les classeurs PowerPivot que vous approuvez.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Cliquez sur **Oui** pour activer les requêtes.  
  
 Vous pouvez également modifier les paramètres de configuration de façon à ne plus avertir lors de l'actualisation des données :  
  
1.  Dans l'Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur **Application Excel Services**.  
  
3.  Cliquez sur **Emplacement de fichier approuvé**.  
  
4.  Cliquez sur **http://** ou sur l’emplacement que vous voulez configurer.  
  
5.  Dans Données externes, désactivez la case à cocher **Avertir lors de l'actualisation**.  
  
6.  Cliquez sur **OK**.  
  
 Vous pouvez également créer un emplacement approuvé pour les sites qui contiennent des classeurs PowerPivot, puis modifier les paramètres de configuration uniquement pour ce site. Pour plus d'informations, consultez [Créer un emplacement approuvé pour les sites PowerPivot dans l'Administration centrale](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
