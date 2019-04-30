---
title: Paramètres du projet (Azure SQL DB) (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8c06420a-533b-4de0-948d-a0c6b368c544
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e0c16fe617b5808f22f15cdf89af8dc7a1e79898
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63311987"
---
# <a name="project-settings-azure-sql-db-mysqltosql"></a>Paramètres du projet (Azure SQL DB) (MySQLToSQL)
Les paramètres de projet SQL Azure vous permettent de configurer le suffixe de la base de données SQL Azure à ajouter dans la boîte de dialogue de connexion et permettent également à implémenter le mécanisme de pulsation dans la connexion de SQL Azure.  
  
Le volet SQL Azure est disponible dans le **paramètres du projet** et **par défaut des paramètres de projet** boîtes de dialogue.  
  
-   Utilisez la boîte de dialogue Paramètres du projet pour définir les options de configuration pour le projet actuel. Accéder aux paramètres de SQL Azure, sur le **outils** menu, sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis sélectionnez **SQL Azure**.  
  
-   Utilisez la boîte de dialogue Paramètres du projet par défaut pour définir les options de configuration pour tous les projets. Accéder aux paramètres de SQL Azure, sur le **outils** menu, sélectionnez **DefaultProject paramètres**, sélectionnez le type de projet de migration SQL Azure à partir de **Version cible de Migration** drop jusqu'à accès les paramètres dans le volet SQL Azure, cliquez sur **général** en bas du volet gauche, puis sélectionnez **SQL Azure**.  
  
## <a name="options"></a>Options  
  
## <a name="connectivity"></a>Connectivité  
**Intervalle de pulsation**  
  
Spécifie un intervalle de temps à utiliser pour le mécanisme de pulsation afin de maintenir la connexion SQL Azure dans ' minutes : format de secondes.  
  
**Valeur par défaut**: 4 » : 45'  
  
La valeur doit être spécifiée dans suis : format des ss (par exemple, ' 4:45 ' ou ' 0:50 ').  
  
**Suffixe du serveur SQL Azure**  
  
Spécifie le suffixe du serveur SQL Azure  
  
**Valeur par défaut**: 'database.windows.net'.  
  
