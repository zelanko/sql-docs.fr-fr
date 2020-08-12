---
title: Définir les valeurs par défaut des définitions de trace
titleSuffix: SQL Server Profiler
description: Découvrez comment utiliser SQL Server Profiler pour configurer les modèles utilisés par défaut par SQL Server et Analysis Services pour chaque fournisseur ou serveur.
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: ab9fc570-797d-411e-814f-1c46d2d5feae
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 48728a7557edc0d2ddfa5d3e1dbf3e9acb868aa7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85726849"
---
# <a name="set-trace-definition-defaults-sql-server-profiler"></a>Définir des paramètres par défaut de trace (SQL Server Profiler)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Le paramètre par défaut de définition de trace est le modèle de trace par défaut utilisé par chaque fournisseur ou serveur. Vous pouvez remplacer les modèles de trace par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
### <a name="to-set-trace-definition-defaults"></a>Pour définir les valeurs par défaut des définitions de trace  
  
1.  Dans le menu **Fichier** , sélectionnez **Modèles**, puis cliquez sur **Modifier le modèle**.  
  
2.  Dans la boîte de dialogue **Propriétés du modèle de trace** , sous l’onglet **Général**, sélectionnez un type de serveur dans la liste **Sélectionner le type de serveur**.  
  
3.  Dans la liste **Sélectionner le nom du modèle**, sélectionnez le nom du modèle à utiliser comme paramètre par défaut de définition de trace.  
  
4.  Sélectionnez **Utiliser comme modèle par défaut pour le type de serveur sélectionné**.  
  
5.  Si nécessaire, cliquez sur l’onglet **Sélection des événements**pour modifier le modèle.  
  
6.  Cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du Générateur de profils SQL Server](../../tools/sql-server-profiler/sql-server-profiler-templates.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
