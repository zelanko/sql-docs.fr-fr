---
title: 'Étape 2 : Appeler le programme serveur (didacticiel RDS) | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], invoking server program
ms.assetid: 5e74c2da-65ee-4de4-8b41-6eac45c3632e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4a1653f2ff0c8cae39b9eecd78aad7a83b03062c
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66699318"
---
# <a name="step-2-invoke-the-server-program-rds-tutorial"></a>Étape 2 : Appeler le programme serveur (tutoriel RDS)
Lorsque vous appelez une méthode sur le client *proxy*, le programme sur le serveur qui exécute la méthode. Dans cette étape, vous allez exécuter une requête sur le serveur.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 **Partie A** si vous n’utilisiez pas [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) dans ce didacticiel, la méthode la plus pratique d’effectuer cette étape consisterait à utiliser le [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet. Le **RDS. DataControl** combine l’étape précédente de création d’un proxy, avec cette étape, en émettant la requête.  
  
 Définir le **RDS. DataControl** objet [Server](../../../ado/reference/rds-api/server-property-rds.md) propriété pour identifier où le programme du serveur doit être instancié ; le [Connect](../../../ado/reference/rds-api/connect-property-rds.md) propriété pour spécifier la chaîne de connexion pour accéder à la source de données ; et le [SQL](../../../ado/reference/rds-api/sql-property.md) propriété pour spécifier le texte de commande de requête. Puis exécutez le [Actualiser](../../../ado/reference/rds-api/refresh-method-rds.md) méthode pour forcer le programme de serveur pour vous connecter à la source de données, récupérer les lignes spécifiées par la requête et retourner un **Recordset** objet au client.  
  
 Ce didacticiel n’utilise pas le **RDS. DataControl**, mais il s’agit d’aspect si c’était le cas :  
  
```vb
Sub RDSTutorial2A()  
   Dim DC as New RDS.DataControl  
   DC.Server = "https://yourServer"  
   DC.Connect = "DSN=Pubs"  
   DC.SQL = "SELECT * FROM Authors"  
   DC.Refresh  
...  
```  
  
 Ni le didacticiel appeler RDS avec des objets ADO, mais il s’agit d’aspect si c’était le cas :  
  
```vb
Dim rs as New ADODB.Recordset  
rs.Open "SELECT * FROM Authors","Provider=MS Remote;Data Source=Pubs;" & _  
        "Remote Server=https://yourServer;Remote Provider=SQLOLEDB;"  
```  
  
 **Partie B** la méthode générale de cette étape consiste à appeler le **RDSServer.DataFactory** objet [requête](../../../ado/reference/rds-api/query-method-rds.md) (méthode). Cette méthode prend une chaîne de connexion qui est utilisé pour se connecter à une source de données, et un texte de commande, qui est utilisé pour spécifier les lignes à retourner à partir de la source de données.  
  
 Ce didacticiel utilise le **DataFactory** objet **requête** méthode :  
  
```vb
Sub RDSTutorial2B()  
   Dim DS as New RDS.DataSpace  
   Dim DF  
   Dim RS as ADODB.Recordset  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "https://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Serveur obtient un objet Recordset (didacticiel RDS)](../../../ado/guide/remote-data-service/step-3-server-obtains-a-recordset-rds-tutorial.md)   
 [Didacticiel RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
