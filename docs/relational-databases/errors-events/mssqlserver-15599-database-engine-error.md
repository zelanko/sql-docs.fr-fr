---
description: MSSQLSERVER_15599
title: MSSQLSERVER_15599 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eca555fb3ced04a0258db78c89c53e8cef9d9c20
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88333815"
---
# <a name="mssqlserver_15599"></a>MSSQLSERVER_15599
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|15599|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SEC_LOCAL_TEMP_AUDIT_PERMISSIONS|  
|Texte du message|Impossible de définir l'audit et des autorisations sur des objets temporaires locaux.|  
  
## <a name="explanation"></a>Explication  
L'audit et les autorisations n'ont aucun effet une fois définis pour les objets temporaires locaux ou globaux. Les instructions ne provoquent pas une erreur (les opérations réussissent), mais n'ont aucun effet.  
  
Ce comportement n'a pas changé, mais à partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], ce message d'information avertit l'utilisateur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Aucune action n'est nécessaire, mais envisagez de supprimer les instructions qui essaient de définir l'audit ou des autorisations sur les objets temporaires locaux ou globaux.  
  
