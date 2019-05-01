---
title: Paramètres du projet (Azure SQL DB) (AccessToSQL) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 2307a62c05503a231c3ee16b79efb25e964f55bd
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63453469"
---
# <a name="project-settings-azure-sql-db-accesstosql"></a>Paramètres du projet (Azure SQL DB) (AccessToSQL)
Les paramètres de projet SQL Azure vous permettent de configurer le suffixe de la base de données SQL Azure à ajouter dans la boîte de dialogue de connexion et permettent également à implémenter le mécanisme de pulsation dans la connexion de SQL Azure.  
  
Le volet SQL Azure est disponible dans le **paramètres du projet** et **par défaut des paramètres de projet** boîtes de dialogue.  
  
-   Utilisez la boîte de dialogue Paramètres du projet pour définir les options de configuration pour le projet actuel. Accéder aux paramètres de SQL Azure, sur le **outils** menu, sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis sélectionnez **SQL Azure**.  
  
-   Utilisez la boîte de dialogue Paramètres du projet par défaut pour définir les options de configuration pour tous les projets. Accéder aux paramètres de SQL Azure, sur le **outils** menu, sélectionnez **DefaultProject paramètres**, sélectionnez le type de projet en tant que « SQL Azure » dans **Version cible de Migration** zone de liste déroulante accéder aux paramètres dans le volet de SQL Azure, cliquez sur **général** en bas du volet gauche, puis sélectionnez **SQL Azure**.  
  
## <a name="options"></a>Options  
  
## <a name="connectivity"></a>Connectivité  
**Intervalle de pulsation**  
  
Spécifie un intervalle de temps à utiliser pour le mécanisme de pulsation afin de maintenir la connexion SQL Azure dans ' minutes : format de secondes.  
  
**Valeur par défaut**: 4 » : 45'  
  
La valeur doit être spécifiée dans suis : format des ss (par exemple, ' 4:45 ' ou ' 0:50 ').  
  
**Suffixe du serveur SQL Azure**  
  
Spécifie le suffixe du serveur SQL Azure  
  
**Valeur par défaut**: 'database.windows.net'.  
  
