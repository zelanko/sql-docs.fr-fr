---
title: Anticipation des erreurs | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- anticipating errors [ADO]
- errors [ADO], preventing
- preventing errors [ADO]
ms.assetid: ea1d4a97-58c3-476b-a496-cc80db2a90d5
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 359dc6c1bd396a0909aea36c5039a4ba5195f326
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="anticipating-errors"></a>Anticipation des erreurs
Prévention des erreurs est au moins aussi importante que la gestion des erreurs. Cette dernière section contient une courte liste des précautions de que votre application peut prendre pour faciliter les erreurs éventuelles.  
  
 Vérifiez l’état des objets en vérifiant la valeur la **état** propriété avant d’essayer d’effectuer une opération à l’aide de ces objets. Par exemple, si votre application utilise un global **connexion**, vérifiez son **état** propriété pour voir si elle est déjà ouverte avant d’appeler le **ouvrir** (méthode).  
  
-   Tout programme qui accepte les données à partir d’un utilisateur doit inclure du code pour valider que les données avant de les envoyer au magasin de données. Vous ne pouvez pas compter sur le magasin de données, le fournisseur, ADO ou même votre langage de programmation pour vous avertir des problèmes. Vous devez vérifier chaque octet entré par vos utilisateurs, vous assurer que les données sont du type correct pour son champ et que les champs obligatoires ne sont pas vides.  
  
 Vérifiez les données avant d’essayer d’écrire des données dans le magasin de données. Le moyen le plus simple pour ce faire consiste à gérer le **WillMove** événement ou la **WillUpdateRecordset** événement. Pour plus d’informations sur la gestion d’événements ADO, consultez [gestion des événements ADO](../../../ado/guide/data/handling-ado-events.md).  
  
 Assurez-vous que **Recordset** objets ne sont pas au-delà des limites de la **Recordset** avant de tenter de déplacer le pointeur. Si vous essayez **MoveNext** lorsque **EOF** a la valeur True ou **MovePrev** lorsque **BOF** a la valeur True, une erreur se produit. Si vous effectuez l’une de la **déplacer** méthodes lorsque les deux **EOF** et **BOF** ont la valeur True, une erreur sera générée.  
  
 Erreurs seront produisent si vous essayez d’effectuer des opérations telles que **recherche** et **trouver** sur vide **Recordset**.

