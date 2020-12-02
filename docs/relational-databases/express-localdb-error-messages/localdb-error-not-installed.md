---
description: LOCALDB_ERROR_NOT_INSTALLED
title: LOCALDB_ERROR_NOT_INSTALLED | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: e7912885-1c14-409b-9022-83ad4c36f3bd
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 5fbc51b2c3e4efc75200bbeef211979956d1cb5c
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96506165"
---
# <a name="localdb_error_not_installed"></a>LOCALDB_ERROR_NOT_INSTALLED
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Détails  
  
| Attribut | Valeur |
| --------- | ----- |
|Nom du produit|SQL Server|  
|ID de l’événement|278|  
|Source de l’événement|Runtime de base de données locale SQL Server 12.0|  
|Composant|API d'exécution de la base de données locale|  
|Texte du message|Remarque : le texte du message est vide, car ce message signifie que la totalité de l’API de base de données locale (y compris la fonction FormatMessage qui mappe HRESULTS dans le texte du message) n’est pas disponible.|  
  
## <a name="explanation"></a>Explication  
 L'instance d'exécution de base de données locale n'est pas installée sur l'ordinateur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Installez le runtime de la base de données locale et recommencez l'opération.  
  
  
