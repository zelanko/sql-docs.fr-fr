---
title: MARS (Multiple Active Result Sets)
description: Décrit comment avoir plusieurs instances SqlDataReader ouvertes sur une connexion lorsque chaque instance de SqlDataReader est démarrée à partir d’une commande distincte.
ms.date: 08/15/2019
ms.assetid: c90ef863-bac7-44cf-adc1-f05c36fcf57d
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 60c27bd94162b4d6bf4d7370218e1fa7781e6491
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247697"
---
# <a name="multiple-active-result-sets-mars"></a>MARS (Multiple Active Result Sets)

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

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
