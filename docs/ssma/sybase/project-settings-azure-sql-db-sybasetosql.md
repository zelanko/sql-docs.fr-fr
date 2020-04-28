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
ms.openlocfilehash: 829e7b0c51cd341193944fb2f28241f48618c407
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "70176226"
---
# <a name="project-settings-azure-sql-db--sybasetosql"></a>Paramètres du projet (Azure SQL DB) (SybaseToSQL)
Les paramètres de projet de base de données SQL Azure vous permettent de configurer le suffixe de base de données Azure SQL Database à ajouter dans la boîte de dialogue de connexion et d’autoriser également l’implémentation d’un mécanisme de pulsation dans une connexion Azure SQL DB.  
  
Le volet base de code SQL Azure est disponible dans les boîtes de dialogue **paramètres du projet** et **paramètres du projet par défaut** .  
  
-   Utilisez la boîte de dialogue Paramètres du projet pour définir les options de configuration du projet actif. Pour accéder aux paramètres d’Azure SQL DB, dans le menu **Outils** , sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis sélectionnez **base de SQL Azure**.  
  
-   Utilisez la boîte de dialogue Paramètres du projet par défaut pour définir les options de configuration de tous les projets. Pour accéder aux paramètres d’Azure SQL Database, dans le menu **Outils** , sélectionnez **paramètres DefaultProject**, cliquez sur **général** en bas du volet gauche, puis sélectionnez **Azure SQL DB**.  
  
## <a name="connectivity"></a>Connectivité  
**Intervalle de pulsation**  
  
Spécifie un intervalle de temps à utiliser pour le mécanisme de pulsation afin de conserver la connexion Azure SQL DB active en « minutes : secondes ».  
  
**Valeur par défaut**: « 4:45 »  
  
La valeur doit être spécifiée au format « m :SS » (par exemple, « 4:45 » ou « 0:50 »).  
  
**Suffixe du serveur Azure SQL DB**  
  
Spécifie un suffixe de serveur Azure SQL DB  
  
**Valeur par défaut**: 'Database.Windows.net'.  
  
