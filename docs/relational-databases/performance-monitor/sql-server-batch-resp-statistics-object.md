---
title: SQL Server, objet Batch Resp Statistics | Microsoft Docs
description: Découvrez l’objet de performance SQLServer:Batch Resp Statistics, qui fournit des compteurs pour suivre les temps de réponse des lots SQL Server.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Batch Resp Statistics
ms.assetid: a58e8733-6a8d-4b47-b5cb-042e813d808a
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 155ff6d21fdb0a40e042463b809c1ed14bbe70df
ms.sourcegitcommit: a49a66dbda0cb16049e092b49c8318ac3865af3c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94983160"
---
# <a name="sql-server-batch-resp-statistics-object"></a>SQL Server, Objet Batch Resp Statistics
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
L’objet de performance **SQLServer:Batch Resp Statistics** fournit des compteurs pour suivre les temps de réponse de lot SQL Server.

Le tableau suivant décrit les objets de performance **Batch Resp Statistics** SQL Server.


|**Compteurs Batch Resp Statistics SQL Server**|Description|  
|-------------|-----------------|  
|**Lots >=000000ms & \<000001ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 0 ms mais inférieur à 1 ms|
|**Lots >=000001ms & \<000002ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 1 ms mais inférieur à 2 ms|
|**Lots >=000002ms & \<000005ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 2 ms mais inférieur à 5 ms|
|**Lots >=000005ms & \<000010ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 5 ms mais inférieur à 10 ms|
|**Lots >=000010ms & \<000020ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 10 ms mais inférieur à 20 ms|
|**Lots >=000020ms & \<000050ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 20 ms mais inférieur à 50 ms|
|**Lots >=000050ms & \<000100ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 50 ms mais inférieur à 100 ms|
|**Lots >=000100ms & \<000200ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 100 ms mais inférieur à 200 ms|
|**Lots >=000200ms & \<000500ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 200 ms mais inférieur à 500 ms|
|**Lots >=000500ms & \<001000ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 500 ms mais inférieur à 1 000 ms|
|**Lots >=001000ms & \<002000ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 1 000 ms mais inférieur à 2 000 ms|
|**Lots >=002000ms & \<005000ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 2 000 ms mais inférieur à 5 000 ms|
|**Lots >=005000ms & \<010000ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 5 000 ms mais inférieur à 10 000 ms|
|**Lots >=010000ms & \<020000ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 10 000 ms mais inférieur à 20 000 ms|
|**Lots >=020000ms & \<050000ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 20 000 ms mais inférieur à 50 000 ms|
|**Lots >=050000ms & \<100000ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 50 000 ms mais inférieur à 100 000 ms| 
|**Batches >=100000ms**|Nombre de lots SQL dont le temps de réponse est supérieur ou égal à 100 000 ms| 

Chaque compteur de l'objet contient les instances suivantes :  
  
|Élément|Description|  
|----------|-----------------|  
|**Temps processeur:Demandes**|Nombre de demandes basées sur le temps processeur.|  
|**Temps processeur:Total(ms)**|Le temps total passé par le processeur sur le lot.|  
|**Temps écoulé:Demandes**|Nombre de demandes basées sur le temps écoulé.|  
|**Temps écoulé:Total(ms)**|Le temps écoulé du lot.|  

## <a name="see-also"></a>Voir aussi
[SQL Server, objet Plan Cache](../../relational-databases/performance-monitor/sql-server-plan-cache-object.md)  
[Analyser l'utilisation des ressources (Moniteur système)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
