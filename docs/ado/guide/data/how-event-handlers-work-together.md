---
title: Fonctionnement conjoint des gestionnaires d’événements | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO], about event handlers
- unpaired event handlers [ADO]
- paired event handlers [ADO]
- single event handlers [ADO]
- event handlers [ADO]
- multiple object event handlers [ADO]
ms.assetid: a86c8a02-dd69-420d-8a47-0188b339858d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a575e4df609430d5dc71517032f4c3da739bba24
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47613307"
---
# <a name="how-event-handlers-work-together"></a>Fonctionnement conjoint des gestionnaires d’événements
Sauf si vous programmez en Visual Basic, tous les gestionnaires d’événements pour **connexion** et **Recordset** événements doivent être implémentés, que vous en fait de traiter ou non tous les événements. La quantité de travail d’implémentation que vous avez à faire dépend de votre langage de programmation. Pour plus d’informations, consultez [instanciation des événements ADO par langage](../../../ado/guide/data/ado-event-instantiation-by-language.md).  
  
## <a name="paired-event-handlers"></a>Gestionnaires d’événements associés  
 Chaque gestionnaire d’événements s’est associé à un **Terminer** Gestionnaire d’événements. Par exemple, lorsque votre application modifie la valeur d’un champ, la **WillChangeField** Gestionnaire d’événements est appelé. Si la modification est acceptable, l’application conserve le **ne** paramètre inchangé et l’opération est effectuée. Lorsque l’opération se termine, un **FieldChangeComplete** événement informe votre application que l’opération est terminée. Si elle a réussi, **ne** contient **adStatusOK**; sinon, **ne** contient **contraire** et Vous devez vérifier le **erreur** objet pour déterminer la cause de l’erreur.  
  
 Lorsque **WillChangeField** est appelée, vous pouvez déterminer que la modification ne doit pas être effectuée. Dans ce cas, définissez **ne** à **adStatusCancel.** L’opération est annulée et le **FieldChangeComplete** événement reçoit un **ne** valeur **contraire**. Le **erreur** objet contient **adErrOperationCancelled** afin que votre **FieldChangeComplete** Gestionnaire sait que l’opération a été annulée. Toutefois, vous devez vérifier la valeur de la **ne** paramètre avant de le modifier, car la définition **ne** à **adStatusCancel** n’a aucun effet si le paramètre a été défini. pour **adStatusCantDeny** sur ENTRÉE pour la procédure.  
  
 Parfois, une opération peut déclencher plusieurs événements. Par exemple, le **Recordset** objet a associé pour les événements **champ** modifications et **enregistrement** modifications. Quand votre application change la valeur d’un **champ**, le **WillChangeField** Gestionnaire d’événements est appelé. S’il détermine que l’opération puisse continuer, le **WillChangeRecord** Gestionnaire d’événements est également déclenché. Si ce gestionnaire autorise également l’événement à continuer, la modification est apportée et la **FieldChangeComplete** et **RecordChangeComplete** gestionnaires d’événements sont appelés. L’ordre dans lequel les gestionnaires d’événements sera pour une opération particulière sont appelées n’est pas défini, vous devez éviter d’écrire du code qui dépend de l’appel de gestionnaires dans une séquence particulière.  
  
 Dans les instances lorsque plusieurs événements Will sont déclenchés, l’un des événements peut annuler l’opération en attente. Par exemple, lorsque votre application modifie la valeur d’un **champ**, à la fois **WillChangeField** et **WillChangeRecord** devrait être appelés gestionnaires d’événements. Toutefois, si l’opération est annulée dans le premier gestionnaire d’événements qui lui sont associé **Terminer** gestionnaire est appelé immédiatement avec **adStatusOperationCancelled**. Le second gestionnaire n’est jamais appelé. Si, toutefois, le premier gestionnaire d’événements permet de continuer, l’autre gestionnaire d’événements est appelé. S’il annule ensuite l’opération, les deux **Terminer** événements sont appelés comme dans les exemples précédents.  
  
## <a name="unpaired-event-handlers"></a>Gestionnaires d’événements non appariés  
 Tant que l’état passé à l’événement n’est pas **adStatusCantDeny**, vous pouvez désactiver les notifications d’événements pour n’importe quel événement en retournant **adStatusUnwantedEvent** dans le *état*paramètre. Par exemple, lorsque votre **Terminer** Gestionnaire d’événements est appelé la première fois, vous pouvez retourner **adStatusUnwantedEvent**. Vous recevrez ensuite uniquement **sera** événements. Toutefois, certains événements peuvent être déclenchés pour plusieurs raisons. Dans ce cas, l’événement aura un *raison* paramètre. Lorsque vous revenez **adStatusUnwantedEvent**, vous cesserez de recevoir des notifications pour cet événement uniquement lorsqu’ils se produisent pour cette raison particulière. En d’autres termes, vous recevrez potentiellement notification pour chaque raison possible est que l’événement peut être déclenchée.  
  
 Seul **sera** gestionnaires d’événements peuvent être utiles lorsque vous souhaitez examiner les paramètres qui seront utilisés dans une opération. Vous pouvez modifier ces paramètres d’opération ou annuler l’opération.  
  
 Vous pouvez également laisser **Terminer** notification d’événement. Lorsque le premier gestionnaire d’événements Will est appelé, retournez **adStatusUnwantedEvent**. Vous recevrez ensuite uniquement **Terminer** événements.  
  
 Seul **Terminer** gestionnaires d’événements peuvent être utiles pour la gestion des opérations asynchrones. Chaque opération asynchrone a approprié **Terminer** événement.  
  
 Par exemple, il peut prendre beaucoup de temps pour remplir un grand [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet. Si votre application est correctement écrit, vous pouvez démarrer un `Recordset.Open(...,adAsyncExecute)` opération et continuer à d’autres traitements. Vous finiront par être averti lorsque le **Recordset** est rempli par un **ExecuteComplete** événement.  
  
## <a name="single-event-handlers-and-multiple-objects"></a>Gestionnaires d’événements unique et plusieurs objets  
 La souplesse d’un langage de programmation comme Microsoft Visual C++® vous permet de disposer d’un gestionnaire d’événements processus événements à partir de plusieurs objets. Par exemple, vous pouvez avoir un **déconnexion** événement Gestionnaire traiter les événements à partir de plusieurs **connexion** objets. Si l’une des connexions s’est terminée, le **déconnexion** Gestionnaire d’événements est appelé. Vous pouvez demander quelle connexion a provoqué l’événement, car le paramètre d’objet de gestionnaire d’événements définiriez correspondant **connexion** objet.  
  
> [!NOTE]
>  Cette technique ne peut pas être utilisée dans Visual Basic, car ce langage peut mettre en corrélation qu’un seul objet à un gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Résumé du Gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Instanciation des événements ADO par langage](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Paramètres d’événement](../../../ado/guide/data/event-parameters.md)   
 [Types d’événements](../../../ado/guide/data/types-of-events.md)
