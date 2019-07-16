---
title: Modifier le mappage de Type (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 184f7ab2-725f-491e-a15b-b889f2fb6a68
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: d31304dae7246e425ef54af6d1382af7e885696c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102998"
---
# <a name="edit-type-mapping-mysqltosql"></a>Modifier le mappage de type (MySQLToSQL)
Le **modifier le mappage de Type** boîte de dialogue vous permet de spécifier comment les types sont mappés entre les objets de base de données source et de destination.  
  
Vous pouvez accéder à cette boîte de dialogue à plusieurs endroits :  
  
-   Lorsque vous sélectionnez une base de données source ou un objet de base de données, le **le mappage de Type** onglet s’affiche à droite de l’Explorateur de métadonnées. Cliquez sur **ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
-   Sur le **outils** menu, sélectionnez **paramètres du projet** ou **par défaut des paramètres de projet**. Dans la boîte de dialogue, sélectionnez **le mappage de Type**. Cliquez sur **ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
-   Mappages de types de table spécifiques de remplacent la base de données et les mappages de type de projet. Mappages spécifiques à la base de données remplacent les mappages de projet.  
  
## <a name="options"></a>Options  
  
##### <a name="source-type"></a>Type de source  
Sélectionnez le type de données source à mapper à un type de données SQL Server.  
  
Si le type de données est de longueur variable, les champs suivants seront affiche sous **Sourcetype**:  
  
##### <a name="from"></a>From  
Spécifiez la longueur minimale pour ce mappage. Par exemple, pour le **nchar** type de données, vous pouvez entrer 10 pour spécifier que ce mappage est pour une plage commençant à **nchar(10).**  
  
##### <a name="to"></a>Pour  
Spécifiez la longueur maximale pour ce mappage. Par exemple, pour le **nchar** type de données, vous pouvez entrer 20 pour spécifier que ce mappage s’applique à une plage et se termine au **nchar (20).**  
  
##### <a name="target-type"></a>Type de cible  
Sélectionnez le type de données SQL Server à laquelle le type de données source est mappé. Lorsque SSMA crée la table ou dans SQL Server, le type de source de données changera à ce type de données.  
  
Si le type de données est de longueur variable, le champ suivant apparaît sous **type cible**:  
  
##### <a name="replace-with"></a>Remplacer par  
Spécifier la longueur de la cible pour ce mappage. Par exemple, pour le **nvarchar** type de données, vous pouvez entrer 20 pour spécifier que le type de données source spécifiée doit être mappé à **nvarchar (20).**  
  
