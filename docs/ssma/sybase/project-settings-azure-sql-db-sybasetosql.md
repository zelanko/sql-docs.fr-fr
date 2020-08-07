---
title: Paramètres du projet (Azure SQL Database) (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 57002374-0d4d-43c1-b4e9-cbec02355a9c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 0348d548d21ea9b593aa7fe4aa14986607ba76fb
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87863441"
---
# <a name="project-settings-azure-sql-database--sybasetosql"></a>Paramètres du projet (Azure SQL Database) (SybaseToSQL)
Les paramètres du projet Azure SQL Database vous permettent de configurer l’ajout du suffixe de base de données Azure SQL Database dans la boîte de dialogue de connexion et d’autoriser également l’implémentation d’un mécanisme de pulsation dans Azure SQL Database connexion.  
  
Le volet Azure SQL Database est disponible dans les boîtes de dialogue **paramètres du projet** et **paramètres du projet par défaut** .  
  
-   Utilisez la boîte de dialogue Paramètres du projet pour définir les options de configuration du projet actif. Pour accéder aux paramètres de Azure SQL Database, dans le menu **Outils** , sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis sélectionnez **Azure SQL Database**.  
  
-   Utilisez la boîte de dialogue Paramètres du projet par défaut pour définir les options de configuration de tous les projets. Pour accéder aux paramètres de Azure SQL Database, dans le menu **Outils** , sélectionnez **paramètres DefaultProject**, cliquez sur **général** en bas du volet gauche, puis sélectionnez **Azure SQL Database**.  
  
## <a name="connectivity"></a>Connectivité  
**Intervalle de pulsation**  
  
Spécifie un intervalle de temps à utiliser pour le mécanisme de pulsation afin que la connexion Azure SQL Database reste active en « minutes : secondes ».  
  
**Valeur par défaut**: « 4:45 »  
  
La valeur doit être spécifiée au format « m :SS » (par exemple, « 4:45 » ou « 0:50 »).  
  
**Suffixe du serveur Azure SQL Database**  
  
Spécifie un suffixe de serveur Azure SQL Database  
  
**Valeur par défaut**: 'Database.Windows.net'.  
  
