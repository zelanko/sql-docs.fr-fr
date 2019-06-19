---
title: Paramètres du projet (Azure SQL DB) (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 57002374-0d4d-43c1-b4e9-cbec02355a9c
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 14fa0cb949505ab2aeb15d1236add9acba9a1ab1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62703728"
---
# <a name="project-settings-azure-sql-db--sybasetosql"></a>Paramètres du projet (Azure SQL DB) (SybaseToSQL)
Les paramètres de projet de base de données SQL Azure vous permettent de configurer le suffixe de base de données de base de données SQL Azure à ajouter dans la boîte de dialogue de connexion et permettent également à implémenter le mécanisme de pulsation dans la connexion de base de données SQL Azure.  
  
Le volet de la base de données SQL Azure est disponible dans le **paramètres du projet** et **par défaut des paramètres de projet** boîtes de dialogue.  
  
-   Utilisez la boîte de dialogue Paramètres du projet pour définir les options de configuration pour le projet actuel. Pour accéder aux paramètres de base de données SQL Azure, sur le **outils** menu, sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis sélectionnez  **Base de données SQL Azure**.  
  
-   Utilisez la boîte de dialogue Paramètres du projet par défaut pour définir les options de configuration pour tous les projets. Pour accéder aux paramètres de base de données SQL Azure, sur le **outils** menu, sélectionnez **DefaultProject paramètres**, cliquez sur **général** en bas de la partie gauche, puis sélectionnez **Azure SQL DB**.  
  
## <a name="connectivity"></a>Connectivité  
**Intervalle de pulsation**  
  
Spécifie un intervalle de temps à utiliser pour le mécanisme de pulsation afin de maintenir la connexion de base de données SQL Azure dans ' minutes : format de secondes.  
  
**Valeur par défaut**: 4 » : 45'  
  
La valeur doit être spécifiée dans suis : format des ss (par exemple, ' 4:45 ' ou ' 0:50 ').  
  
**Suffixe de serveur de base de données SQL Azure**  
  
Spécifie un suffixe de serveur de base de données SQL Azure  
  
**Valeur par défaut**: 'database.windows.net'.  
  
