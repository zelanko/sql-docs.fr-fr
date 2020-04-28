---
title: Connection, objet (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection
helpviewer_keywords:
- Connection object [ADO]
ms.assetid: ef6b1824-5b12-43db-89d7-8f3d13896d4d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 278e2d90ed20b99706f00acf72e2892941c42865
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67933563"
---
# <a name="connection-object-ado"></a>Connection, objet (ADO)
Représente une connexion ouverte à une source de données.  
  
## <a name="remarks"></a>Notes  
 Un objet **Connection** représente une session unique avec une source de données. Dans un système de base de données client/serveur, il peut être équivalent à une connexion réseau réelle au serveur. Selon les fonctionnalités prises en charge par le fournisseur, certaines collections, méthodes ou propriétés d’un objet de **connexion** peuvent ne pas être disponibles.  
  
 Avec les collections, les méthodes et les propriétés d’un objet **Connection** , vous pouvez effectuer les opérations suivantes :  
  
-   Configurez la connexion avant de l’ouvrir avec les propriétés [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md), [ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)et [mode](../../../ado/reference/ado-api/mode-property-ado.md) . **ConnectionString** est la propriété par défaut de l’objet de **connexion** .  
  
-   Définissez la propriété [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) sur client pour appeler le [service de curseur Microsoft pour OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md), qui prend en charge les mises à jour par lots.  
  
-   Définissez la base de données par défaut pour la connexion avec la propriété [DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md) .  
  
-   Définissez le niveau d’isolation pour les transactions ouvertes sur la connexion à l’aide de la propriété [IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md) .  
  
-   Spécifiez un fournisseur OLE DB avec la propriété [Provider](../../../ado/reference/ado-api/provider-property-ado.md) .  
  
-   Établissez et interrompez ultérieurement la connexion physique à la source de données avec les méthodes [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) et [Close](../../../ado/reference/ado-api/close-method-ado.md) .  
  
-   Exécutez une commande sur la connexion à l’aide de la méthode [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) et configurez l’exécution avec la propriété [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md) .  
  
    > [!NOTE]
    >  Pour exécuter une requête sans utiliser d’objet Command, transmettez une chaîne de requête à la méthode **Execute** d’un objet **Connection** . Toutefois, un objet [Command](../../../ado/reference/ado-api/command-object-ado.md) est requis lorsque vous souhaitez conserver le texte de la commande et le réexécuter, ou utiliser des paramètres de requête.  
  
-   Gérer les transactions sur la connexion ouverte, y compris les transactions imbriquées si le fournisseur les prend en charge, avec les méthodes [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md), [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)et [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) , ainsi que la propriété [attributes](../../../ado/reference/ado-api/attributes-property-ado.md) .  
  
-   Examinez les erreurs retournées par la source de données avec la collection [Errors](../../../ado/reference/ado-api/errors-collection-ado.md) .  
  
-   Lisez la version de l’implémentation ADO utilisée avec la propriété [version](../../../ado/reference/ado-api/version-property-ado.md) .  
  
-   Obtenez des informations de schéma sur votre base de données avec la méthode [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) .  
  
 Vous pouvez créer des objets de **connexion** indépendamment de tout autre objet défini précédemment.  
  
 Vous pouvez exécuter des commandes ou des procédures stockées nommées comme s’il s’agissait de méthodes natives sur un objet de **connexion** , comme indiqué dans la section suivante. Quand une commande nommée porte le même nom que celle d’une procédure stockée, l’appel de « Native Method Call » sur un objet **Connection** exécute toujours la commande nommée au lieu de la procédure stockée.  
  
> [!NOTE]
>  N’utilisez pas cette fonctionnalité (en appelant une commande nommée ou une procédure stockée comme s’il s’agissait d’une méthode native sur l’objet de **connexion** ) dans une application de .NET Framework Microsoft®, car l’implémentation sous-jacente de la fonctionnalité est en conflit avec la façon dont le .NET Framework interagit avec com.  
  
## <a name="execute-a-command-as-a-native-method-of-a-connection-object"></a>Exécuter une commande en tant que méthode native d’un objet Connection  
 Pour exécuter une commande, attribuez un nom à la commande à l’aide de la propriété [nom](../../../ado/reference/ado-api/name-property-ado.md) de l’objet de **commande** . Affectez à la propriété **ActiveConnection** de l’objet **Command** la connexion. Ensuite, émettez une instruction dans laquelle le nom de la commande est utilisé comme s’il s’agissait d’une méthode sur l’objet de **connexion** , suivi de tous les paramètres et d’un objet **Recordset** si des lignes sont retournées. Définissez les propriétés du **Recordset** pour personnaliser le **jeu d’enregistrements**résultant. Par exemple :  
  
```  
Dim cnn As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
...  
cnn.Open "..."  
cmd.Name = "yourCommandName"  
cmd.ActiveConnection = cnn  
...  
'Your command name, any parameters, and an optional Recordset.  
cnn. "parameter", rst  
```  
  
## <a name="execute-a-stored-procedure-as-a-native-method-of-a-connection-object"></a>Exécuter une procédure stockée en tant que méthode native d’un objet de connexion  
 Pour exécuter une procédure stockée, émettez une instruction dans laquelle le nom de la procédure stockée est utilisé comme s’il s’agissait d’une méthode sur l’objet de **connexion** , suivie de n’importe quel paramètre. ADO effectue une « meilleure estimation » des types de paramètres. Par exemple :  
  
```  
Dim cnn As New ADODB.Connection  
...  
'Your stored procedure name and any parameters.  
cnn. "parameter"  
```  
  
 L’objet de **connexion** est sécurisé pour l’écriture de scripts.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Connection](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Errors, collection (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Annexe A : Fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md)
