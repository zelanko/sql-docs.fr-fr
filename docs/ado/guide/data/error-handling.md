---
title: Gestion des erreurs | Documents Microsoft
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
- reporting errors [ADO]
- errors [ADO]
- ADO, error handling
ms.assetid: 4909e413-f3b0-4183-8ad3-67b1434df742
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a1c85fb540f034c5a0a6870c38ea5797948d5fbd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="error-handling"></a>Gestion des erreurs
ADO utilise différentes méthodes pour avertir une application d’erreurs qui se produisent. Cette section présente les types d’erreurs qui peuvent se produire lorsque vous utilisez ADO et comment votre application est notifiée. Il en conclut en faisant des suggestions sur la façon de gérer ces erreurs.  
  
## <a name="how-does-ado-report-errors"></a>Comment ADO ne signale pas les erreurs ?  
 ADO signale les erreurs de plusieurs façons :  
  
-   Erreurs ADO génèrent une erreur d’exécution. Gérer une erreur ADO de la même façon que vous le feriez pour toute autre erreur d’exécution, comme l’utilisation d’un **en cas d’erreur** instruction en Visual Basic.  
  
-   Votre programme peut recevoir des erreurs de OLE DB. Une erreur OLE DB génère une erreur d’exécution.  
  
-   Si l’erreur est spécifique à votre fournisseur de données, un ou plusieurs **erreur** objets sont placés dans le **erreurs** collection de la **connexion** objet qui a été utilisé pour accéder aux données magasin de l’erreur s’est produite.  
  
-   Si le processus qui a déclenché un événement produit également une erreur, les informations d’erreur sont placées dans un **erreur** de l’objet et transmis en tant que paramètre à l’événement. Consultez [gestion des événements ADO](../../../ado/guide/data/handling-ado-events.md) pour plus d’informations sur les événements.  
  
-   Des problèmes qui se produisent lors du traitement par lots mises à jour ou autres opérations en bloc implique un **Recordset** peut être indiquée par le **état** propriété de la **Recordset**. Par exemple, les violations de contraintes de schéma ou des autorisations insuffisantes peuvent être spécifiées par **RecordStatusEnum** valeurs.  
  
-   Problèmes impliquant un particulier **champ** dans l’enregistrement actif sont également signalés par le **état** propriété de chaque **champ** dans le **champs**  collection de la **enregistrement** ou **Recordset**. Par exemple, les types de données incompatible ou les mises à jour qui n’a pas pu être effectuées. peuvent être spécifiés par **FieldStatusEnum** valeurs.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Erreurs ADO](../../../ado/guide/data/ado-errors.md)  
  
-   [Erreurs du fournisseur](../../../ado/guide/data/provider-errors.md)  
  
-   [Informations sur l’erreur de champ](../../../ado/guide/data/field-related-error-information.md)  
  
-   [Informations sur l’erreur Recordset](../../../ado/guide/data/recordset-related-error-information.md)  
  
-   [Gestion des erreurs dans d’autres langages](../../../ado/guide/data/handling-errors-in-other-languages.md)  
  
-   [Anticipation des erreurs](../../../ado/guide/data/anticipating-errors.md)

