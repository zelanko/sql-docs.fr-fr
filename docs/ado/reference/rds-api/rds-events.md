---
description: Événements RDS
title: Événements RDS | Microsoft Docs
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
helpviewer_keywords:
- events [ADO], RDS
- RDS events [ADO]
ms.assetid: e03739e0-8169-46d6-9956-556b644a7645
author: rothja
ms.author: jroth
ms.openlocfilehash: be38e4897e942e30af61937c326cd2efa16a1fd8
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724370"
---
# <a name="rds-events"></a>Événements RDS
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](/dotnet/framework/wcf/).  
  
|Événement|Description|  
|-|-|  
|[onError (RDS)](./onerror-event-rds.md)|Appelé chaque fois qu’une erreur se produit pendant une opération.|  
|[onReadyStateChange (RDS)](./onreadystatechange-event-rds.md)|Appelée chaque fois que la valeur de la propriété **ReadyState** change.|