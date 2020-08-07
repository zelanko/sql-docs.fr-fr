---
title: Modifier le mappage de type (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 184f7ab2-725f-491e-a15b-b889f2fb6a68
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 20c0eda313a16ac1f896a1382b8d7ad3546144f1
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935584"
---
# <a name="edit-type-mapping-mysqltosql"></a>Modifier le mappage de type (MySQLToSQL)
La boîte de dialogue **modifier le mappage de type** vous permet de spécifier la manière dont les types sont mappés entre les objets de base de données source et de destination.  
  
Vous pouvez accéder à cette boîte de dialogue à plusieurs endroits :  
  
-   Lorsque vous sélectionnez une base de données source ou un objet de base de données, l’onglet **mappage de type** s’affiche à droite de l’Explorateur de métadonnées. Cliquez sur **Ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
-   Dans le menu **Outils** , sélectionnez **paramètres du projet** ou paramètres du **projet par défaut**. Dans la boîte de dialogue qui en résulte, sélectionnez **mappage de type**. Cliquez sur **Ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
-   Les mappages de types spécifiques aux tables remplacent les mappages de type de projet et de base de données. Les mappages spécifiques à la base de données remplacent les mappages de projet.  
  
## <a name="options"></a>Options  
  
##### <a name="source-type"></a>Type de source  
Sélectionnez le type de données source à mapper à un type de données SQL Server.  
  
Si le type de données est de longueur variable, les champs suivants s’affichent sous **SourceType**:  
  
##### <a name="from"></a>À partir  
Spécifiez la longueur minimale pour ce mappage. Par exemple, pour le type de données **nchar** , vous pouvez entrer 10 pour spécifier que ce mappage s’adresse à une plage commençant par **nchar (10).**  
  
##### <a name="to"></a>À  
Spécifiez la longueur maximale pour ce mappage. Par exemple, pour le type de données **nchar** , vous pouvez entrer 20 pour spécifier que ce mappage est destiné à une plage se terminant par **nchar (20).**  
  
##### <a name="target-type"></a>Type de cible  
Sélectionnez le type de données SQL Server auquel le type de données source est mappé. Lorsque SSMA crée la table ou dans le SQL Server, le type de données source passe à ce type de données.  
  
Si le type de données est de longueur variable, le champ suivant s’affiche sous **type de cible**:  
  
##### <a name="replace-with"></a>Remplacer par  
Spécifiez la longueur cible pour ce mappage. Par exemple, pour le type de données **nvarchar** , vous pouvez entrer 20 pour spécifier que le type de données source spécifié doit être mappé à **nvarchar (20).**  
  
