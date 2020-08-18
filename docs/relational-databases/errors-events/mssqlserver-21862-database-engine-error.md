---
description: MSSQLSERVER_21862
title: MSSQLSERVER_21862 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d986bf6262940d0f27477be874a2557b2e6a3410
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88332405"
---
# <a name="mssqlserver_21862"></a>MSSQLSERVER_21862
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|MSSQLSERVER|  
|ID de l’événement|21862|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum21862|  
|Texte du message|Les colonnes FILESTREAM ne peuvent pas être publiées dans une publication à l'aide d'une méthode de synchronisation 'database snapshot' ou 'database snapshot character'.|  
  
## <a name="explanation"></a>Explication  
Étant donné qu’il est impossible d’accéder aux données FILESTREAM par le biais d’un instantané de base de données, l’agent d’instantané ne peut pas lire les données FILESTREAM quand le paramètre *database snapshot* ou *database_snapshot_character* est spécifié pour la méthode de synchronisation de la publication.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Modifiez la méthode de synchronisation de publication en sélectionnant un paramètre autre que *database snapshot* ou *database_snapshot_character*, ou excluez simplement la colonne FILESTREAM de la publication.  
  
