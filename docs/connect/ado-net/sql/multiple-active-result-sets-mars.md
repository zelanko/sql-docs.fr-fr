---
title: MARS (Multiple Active Result Sets)
description: Décrit comment avoir plusieurs instances SqlDataReader ouvertes sur une connexion lorsque chaque instance de SqlDataReader est démarrée à partir d’une commande distincte.
ms.date: 08/15/2019
ms.assetid: c90ef863-bac7-44cf-adc1-f05c36fcf57d
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: e93493a28adfecd7dd39c79a86170b06ed18b992
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924291"
---
# <a name="multiple-active-result-sets-mars"></a>MARS (Multiple Active Result Sets)

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

MARS (Multiple Active Result Set) est une fonctionnalité qui permet l’exécution de plusieurs lots sur une connexion unique. Dans les versions précédentes, un seul lot pouvait être exécuté à la fois sur une seule connexion. L’exécution de plusieurs lots avec MARS n’implique pas l’exécution simultanée d’opérations.  
  
## <a name="in-this-section"></a>Contenu de cette section  
[Activation de MARS (Multiple Active Result Sets)](enable-multiple-active-result-sets.md)  
Décrit comment utiliser MARS avec SQL Server.  
  
[Manipulation de données](manipulate-data.md)  
Fournit des exemples de codage d’applications MARS.  
  
## <a name="related-sections"></a>Sections connexes  
[Opérations asynchrones](asynchronous-operations.md)  
Fournit des détails sur l’utilisation des nouvelles fonctionnalités asynchrones dans .NET.  
  
## <a name="next-steps"></a>Étapes suivantes
- [SQL Server et ADO.NET](index.md)
