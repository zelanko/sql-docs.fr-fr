---
title: Paramètres du projet (Azure SQL Database) (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Project Settings dialog box, SQL Azure
- SQL Azure settings
ms.assetid: bbb8a204-d0e4-4f0b-9709-271feb1f136e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 67d80ae6457a4b02e4520d634acfb5f06aa747ec
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823928"
---
# <a name="project-settings-azure-sql-database-accesstosql"></a>Paramètres du projet (Azure SQL Database) (AccessToSQL)
Les paramètres du projet SQL Azure vous permettent de configurer l’ajout du suffixe de base de données SQL Azure dans la boîte de dialogue de connexion et d’autoriser également l’implémentation d’un mécanisme de pulsation dans SQL Azure connexion.  
  
Le volet SQL Azure est disponible dans les boîtes de dialogue **paramètres du projet** et **paramètres du projet par défaut** .  
  
-   Utilisez la boîte de dialogue Paramètres du projet pour définir les options de configuration du projet actif. Pour accéder aux paramètres de SQL Azure, dans le menu **Outils** , sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis sélectionnez **SQL Azure**.  
  
-   Utilisez la boîte de dialogue Paramètres du projet par défaut pour définir les options de configuration de tous les projets. Pour accéder aux paramètres de SQL Azure, dans le menu **Outils** , sélectionnez **paramètres DefaultProject**, sélectionnez le type de projet « SQL Azure » dans la zone de liste déroulante **version cible** de la Migration pour accéder aux paramètres dans SQL Azure volet, cliquez sur **général** en bas du volet gauche, puis sélectionnez **SQL Azure**.  
  
## <a name="options"></a>Options  
  
## <a name="connectivity"></a>Connectivité  
**Intervalle de pulsation**  
  
Spécifie un intervalle de temps à utiliser pour le mécanisme de pulsation afin que la connexion SQL Azure reste active en « minutes : secondes ».  
  
**Valeur par défaut**: « 4:45 »  
  
La valeur doit être spécifiée au format « m :SS » (par exemple, « 4:45 » ou « 0:50 »).  
  
**Suffixe du serveur SQL Azure**  
  
Spécifie le suffixe du serveur SQL Azure  
  
**Valeur par défaut**: 'Database.Windows.net'.  
  
