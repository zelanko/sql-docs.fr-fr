---
title: Commande de flux | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- command streams [ADO]
- streams [ADO], command
ms.assetid: 0ac09dbe-2665-411e-8fbb-d1efe6c777be
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9d1322d872d5e05de4c7f142804fe2f1390b9859
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700884"
---
# <a name="command-streams"></a>Flux de commandes
ADO a toujours pris en charge d’entrée de commande au format de chaîne spécifié par le **CommandText** propriété. Comme alternative, avec ADO 2.7 ou version ultérieure, vous pouvez également utiliser un flux d’informations pour l’entrée de commande en affectant le flux à la **CommandStream** propriété. Vous pouvez affecter une ADO **Stream** objet, ou n’importe quel objet qui prend en charge le modèle COM **IStream** interface.  
  
 Le contenu du flux de commande est simplement transmis à partir d’ADO à votre fournisseur, donc votre fournisseur doit prendre en charge d’entrée de commande par le flux de données pour cette fonctionnalité soit opérationnelle. Par exemple, SQL Server prend en charge les requêtes sous la forme de modèles XML ou OpenXML extensions Transact-SQL.  
  
 Étant donné que les détails du flux de données doivent être interprétés par le fournisseur, vous devez spécifier le dialecte de commande en définissant le **dialecte** propriété. La valeur de **dialecte** est une chaîne qui contient un GUID, qui est défini par votre fournisseur. Pour plus d’informations sur les valeurs valides pour **dialecte** pris en charge par votre fournisseur, consultez la documentation du fournisseur.  
  
## <a name="xml-template-query-example"></a>Exemple de requête de modèle XML  
 L’exemple suivant est écrit en VBScript pour la base de données Northwind.  
  
 Tout d’abord, initialiser et ouvrir le **Stream** objet qui sera utilisé pour contenir le flux de requête :  
  
```  
Dim adoStreamQuery  
Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
adoStreamQuery.Open  
```  
  
 Le contenu du flux de requête sera un modèle de requête XML.  
  
 Le modèle de requête requiert une référence à l’espace de noms XML identifié par le code sql : préfixe de le \<SQL : > balise. Une instruction SQL SELECT est incluse en tant que le contenu du modèle XML et affectée à une variable de chaîne comme suit :  
  
```  
sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME </sql:query>  
</ROOT>"  
```  
  
 Ensuite, écrivez la chaîne dans le flux :  
  
```  
adoStreamQuery.WriteText sQuery, adWriteChar  
adoStreamQuery.Position = 0  
```  
  
 Affecter adoStreamQuery à la **CommandStream** propriété d’un ADO **commande** objet :  
  
```  
Dim adoCmd  
Set adoCmd  = Server.CreateObject("ADODB.Command"")  
adoCmd.CommandStream = adoStreamQuery  
```  
  
 Spécifier la langue de la commande **dialecte**, ce qui indique comment le fournisseur OLE DB de SQL Server doit interpréter le flux de commandes. Le dialecte spécifié par un GUID spécifique au fournisseur :  
  
```  
adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
```  
  
 Enfin, exécutez la requête et renvoyer les résultats à un **Recordset** objet :  
  
```  
Set objRS = adoCmd.Execute  
```
