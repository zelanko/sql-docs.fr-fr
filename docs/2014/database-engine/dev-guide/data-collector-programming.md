---
title: Programmation du collecteur de données | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data collector [SQL Server], programming
ms.assetid: 53b4752b-055d-4716-b2bc-75b4cce84101
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a9a3e4428eee6057ac3e38e553eec43616504a06
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153081"
---
# <a name="data-collector-programming"></a>Programmation du collecteur de données
  L'API du collecteur de données, dans <xref:Microsoft.SqlServer.Management.Collector>, autorise le contrôle par programmation de toutes les opérations de configuration par le biais du modèle objet. Par ailleurs, la plupart des opérations de collecte de données qui utilisent l'API sont implémentées en tant que procédures stockées installées sur le serveur.  
  
 L'illustration suivante montre des éléments clés du modèle objet du collecteur de données.  
  
 ![Le modèle objet de collecteur de données](../../../2014/database-engine/dev-guide/media/dc-objectmodel.gif "le modèle objet de collecteur de données")  
  
  