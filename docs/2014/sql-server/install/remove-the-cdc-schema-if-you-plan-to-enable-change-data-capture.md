---
title: Supprimer le schéma cdc si vous envisagez d’activer la capture de données modifiées | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cdc schema
- change data capture
ms.assetid: 6a84aa25-0f31-4be3-b2dd-4f249b8254ae
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cf7a9173e268b35f5a0a567a0812dc0e0b48ae91
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142416"
---
# <a name="remove-the-cdc-schema-if-you-plan-to-enable-change-data-capture"></a>Supprimez le schéma cdc si vous envisagez d'activer la capture de données modifiées
  Une base de données contient déjà un schéma cdc. Si vous envisagez d'activer la capture de données modifiées après la mise à niveau, vous devez préalablement abandonner ce schéma cdc. Lorsque vous permettez la capture de données modifiées pour une base de données, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] créera un nouveau schéma nommé cdc.  
  
  