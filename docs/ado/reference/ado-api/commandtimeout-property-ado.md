---
title: CommandTimeout, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandTimeout
helpviewer_keywords:
- CommandTimeout property [ADO]
ms.assetid: c611f857-d6b0-4dca-8925-f4a02e769eb0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7c8c6b10e63e4cacce0124eb11102db796168d9b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67919700"
---
# <a name="commandtimeout-property-ado"></a>CommandTimeout, propriété (ADO)
Indique le délai d’attente lors de l’exécution d’une commande avant de mettre fin à la tentative et de générer une erreur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **type long** qui indique, en secondes, le délai d’attente avant l’exécution d’une commande. La valeur par défaut est 30.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **CommandTimeout** sur un objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) ou un objet de [commande](../../../ado/reference/ado-api/command-object-ado.md) pour autoriser l’annulation d’un appel de méthode [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) , en raison de retards du trafic réseau ou de l’utilisation intensive du serveur. Si l’intervalle défini dans la propriété **CommandTimeout** s’écoule avant la fin de l’exécution de la commande, une erreur se produit et ADO annule la commande. Si vous affectez à la propriété la valeur zéro, ADO attend indéfiniment que l’exécution soit terminée. Assurez-vous que le fournisseur et la source de données dans lesquels vous écrivez le code prennent en charge la fonctionnalité **CommandTimeout** .  
  
 Le paramètre **CommandTimeout** sur un **objet Connection** n’a aucun effet sur le paramètre **CommandTimeout** sur un objet **Command** sur la même **connexion**; autrement dit, la propriété **CommandTimeout** de l’objet de **commande** n’hérite pas de la valeur de **CommandTimeout** de l’objet de **connexion** .  
  
 Sur un objet de **connexion** , la propriété **CommandTimeout** reste en lecture/écriture une fois la **connexion** ouverte.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection, objet (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, size et direction, exemple de propriétés (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, size et direction, exemple de propriétés (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, size et direction, exemple de propriétés (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [ConnectionTimeout, propriété (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)
