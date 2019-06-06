---
title: Conservation des données | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: 21c162ca-2845-4dd8-a49d-e715aba8c461
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0f2d47229b7383c11740ca3d7a20ad8e420931a5
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700477"
---
# <a name="persisting-data"></a>Persistance des données
Informatique portable (par exemple, à l’aide d’ordinateurs portables) a généré la nécessité pour les applications qui peuvent s’exécuter dans un état connecté et déconnecté. ADO a ajouté la prise en charge pour ce en donnant au développeur la possibilité d’enregistrer un curseur client **Recordset** sur le disque et recharger ultérieurement.  
  
 Il existe plusieurs scénarios dans lesquels vous pouvez utiliser ce type de fonctionnalité, y compris les éléments suivants :  
  
-   **En déplacement :** Lors de la création de l’application sur la route, il est essentiel de fournir la possibilité d’apporter des modifications et ajouter de nouveaux enregistrements qui peuvent être reconnectées ultérieurement à la base de données et validées.  
  
-   **Recherches rarement mis à jour :** Souvent dans une application, les tables sont utilisées en tant que recherches-par exemple, l’état des tables de taxes. Ils sont rarement mises à jour et sont en lecture seule. Plutôt que de relire ces données à partir du serveur chaque fois que l’application est démarrée, l’application peut simplement charger les données à partir d’un conservé localement **Recordset**.  
  
 Dans ADO, pour enregistrer et charger **Recordsets**, utilisez le **Recordset.Save** et **Recordset.Open(,,,adCmdFile)** méthodes sur ADO **Recordset**objet.  
  
 Vous pouvez utiliser la **Recordset Save** méthode pour conserver votre ADO **Recordset** dans un fichier sur un disque. (Vous pouvez également enregistrer un **Recordset** à ADO **Stream** objet. **Stream** les objets sont abordés plus loin dans le guide.) Une version ultérieure, vous pouvez utiliser la **Open** méthode pour rouvrir la **Recordset** lorsque vous êtes prêt à l’utiliser. Par défaut, ADO enregistre le **Recordset** au format propriétaire Microsoft Advanced Data TableGram (ADTG). Ce format binaire est spécifié à l’aide de la **adPersistADTG PersistFormatEnum** valeur. Vous pouvez également enregistrer votre **Recordset** la sortie au format XML au lieu d’utiliser **adPersistXML**. Pour plus d’informations sur l’enregistrement des jeux d’enregistrements au format XML, consultez [persistance des enregistrements au Format XML](../../../ado/guide/data/persisting-records-in-xml-format.md).  
  
 La syntaxe de la **enregistrer** méthode est la suivante :  
  
```  
  
recordset.  
Save  
Destination, PersistFormat  
  
```  
  
 La première fois que vous enregistrez le **Recordset**, il est facultatif pour spécifier *Destination*. Si vous omettez *Destination*, un nouveau fichier sera créé avec un nom défini sur la valeur de la [Source](../../../ado/reference/ado-api/source-property-ado-recordset.md) propriété de la **Recordset**.  
  
 Omettez *Destination* lorsque vous appelez ensuite **enregistrer** après le premier enregistrement ou une erreur d’exécution se produira. Si vous appelez ensuite **enregistrer** avec un nouveau *Destination*, le **Recordset** est enregistré dans la nouvelle destination. Toutefois, la nouvelle destination et la destination d’origine seront tous deux être ouverts.  
  
 **Enregistrer** ne ferme pas la **Recordset** ou *Destination*, de sorte que vous pouvez continuer à travailler avec le **Recordset** et enregistrer vos modifications les plus récentes. *Destination* reste ouverte jusqu'à ce que le **Recordset** est fermée, au cours de laquelle les autres applications peuvent lire mais pas y écrire *Destination*.  
  
 Pour des raisons de sécurité, le **enregistrer** méthode autorise uniquement l’utilisation des paramètres de sécurité basse et personnalisée à partir d’un script exécuté par Microsoft Internet Explorer.  
  
 Si le **enregistrer** méthode est appelée lors de l’asynchrone **Recordset** extraire, exécuter ou mettre à jour opération est en cours, **enregistrer** attend jusqu'à ce que l’opération asynchrone est Terminer.  
  
 Les enregistrements sont enregistrés en commençant par la première ligne de la **Recordset**. Lorsque le **enregistrer** méthode est terminée, le curseur est déplacé vers la première ligne de la **Recordset**.  
  
 Pour de meilleurs résultats, définissez le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété **adUseClient** avec **enregistrer**. Si votre fournisseur ne prend pas en charge toutes les fonctionnalités nécessaires pour enregistrer les **Recordset** objets, le Service de curseur fournit cette fonctionnalité.  
  
 Quand un **Recordset** est rendue persistante avec le **CursorLocation** propriété définie sur **adUseServer**, la fonctionnalité de mise à jour pour le **Recordset**est limité. En règle générale, seules les mises à jour de la table unique, des insertions et suppressions sont autorisées (dépendent des fonctionnalités de fournisseur). Le [Resync](../../../ado/reference/ado-api/resync-method.md) méthode est également pas disponible dans cette configuration.  
  
 Étant donné que le *Destination* paramètre peut accepter n’importe quel objet prenant en charge OLE DB **IStream** interface, vous pouvez enregistrer un **Recordset** directement à la page ASP  **Réponse** objet.  
  
 Dans l’exemple suivant, le **enregistrer** et **Open** méthodes sont utilisées pour conserver un **Recordset** et la rouvrir plus tard :  
  
```  
'BeginPersist  
   conn.ConnectionString = _  
   "Provider=SQLOLEDB;Data Source=MySQLServer;" _  
      & "Integrated Security=SSPI;Initial Catalog=pubs"  
   conn.Open  
  
   conn.Execute "create table testtable (dbkey int " & _  
      "primary key, field1 char(10))"  
   conn.Execute "insert into testtable values (1, 'string1')"  
  
   Set rst.ActiveConnection = conn  
   rst.CursorLocation = adUseClient  
  
   rst.Open "select * from testtable", conn, adOpenStatic, _  
      adLockBatchOptimistic  
  
   'Change the row on the client  
   rst!field1 = "NewValue"  
  
   'Save to a file--the .dat extension is an example; choose  
   'your own extension. The changes will be saved in the file  
   'as well as the original data.  
   MyFile = Dir("c:\temp\temptbl.dat")  
   If MyFile <> "" Then  
       Kill "c:\temp\temptbl.dat"  
   End If  
  
   rst.Save "c:\temp\temptbl.dat", adPersistADTG  
   Set rst = Nothing  
  
   'Now reload the data from the file  
   Set rst = New ADODB.Recordset  
   rst.Open "c:\temp\temptbl.dat", , adOpenStatic, _  
      adLockBatchOptimistic, adCmdFile  
  
   Debug.Print "After Loading the file from disk"  
   Debug.Print "   Current Edited Value: " & rst!field1.Value  
   Debug.Print "   Value Before Editing: " & rst!field1.OriginalValue  
  
   'Note that you can reconnect to a connection and  
   'submit the changes to the data source  
   Set rst.ActiveConnection = conn  
   rst.UpdateBatch  
'EndPersist  
```  
  
## <a name="remarks"></a>Notes  
 Cette section contient les rubriques suivantes.  
  
-   [En savoir plus sur la persistance des recordsets](../../../ado/guide/data/more-about-recordset-persistence.md)  
  
-   [Persistance des recordsets filtrés et hiérarchiques](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md)  
  
-   [Persistance des enregistrements au format XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
