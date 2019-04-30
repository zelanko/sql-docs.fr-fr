---
title: Les paramètres de Client requis | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
ms.assetid: e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cec3e79e3d37f064cb742588519a374737e01319
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63191809"
---
# <a name="required-client-settings"></a>Paramètres client obligatoires
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Spécifiez les paramètres suivants pour utiliser un personnalisé **DataFactory** gestionnaire.  
  
-   Spécifier « fournisseur = MS Remote » dans la [objet Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) objet [fournisseur de propriété (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) propriété ou le **connexion** chaîne de connexion de l’objet «**Fournisseur**= « mot clé.  
  
-   Définir le [CursorLocation propriété (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété **adUseClient**.  
  
-   Spécifiez le nom du gestionnaire à utiliser dans le [objet DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md) l’objet **gestionnaire** propriété, ou la [objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) chaîne de connexion de l’objet » **Gestionnaire**= « mot clé. (Vous ne pouvez pas définir le gestionnaire le **connexion** objet chaîne de connexion.)  
  
 Services Bureau à distance fournit un gestionnaire par défaut sur le serveur nommé **MSDFMAP. Gestionnaire**. (Le fichier de personnalisation par défaut est nommé MSDFMAP. INI.)  
  
 **Exemple**  
  
 Supposez que les sections suivantes dans **MSDFMAP. INI** et le nom de source de données, AdvWorks, ont été définis précédemment :  
  
```console
[connect CustomerDataBase]  
Access=ReadWrite  
Connect="DSN=AdvWorks"  
  
[sql CustomerById]  
SQL="SELECT * FROM Customers WHERE CustomerID = ?"  
```  
  
 Les extraits de code suivants sont écrits en Visual Basic :  
  
## <a name="rdsdatacontrol-version"></a>RDS. DataControl Version  
  
```vb
Dim dc as New RDS.DataControl  
Set dc.Handler = "MSDFMAP.Handler"  
Set dc.Server = "https://yourServer"  
Set dc.Connect = "Data Source=CustomerDatabase"  
Set dc.SQL = "CustomerById(4)"  
dc.Refresh  
```  
  
## <a name="recordset-version"></a>Version du jeu d’enregistrements  
  
```vb
Dim rs as New ADODB.Recordset  
rs.CursorLocation = adUseClient  
```  
  
 Spécifiez soit le [Gestionnaire de propriété (RDS)](../../../ado/reference/rds-api/handler-property-rds.md) propriété ou un mot clé ; le [fournisseur de propriété (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) propriété ou un mot clé ; et le *CustomerById* et  *CustomerDatabase* identificateurs. Ouvrez ensuite le **Recordset** objet  
  
 rs.Open "CustomerById(4)", "Handler=MSDFMAP.Handler;" & _  
  
```vb
"Provider=MS Remote;Data Source=CustomerDatabase;" & _  
"Remote Server=https://yourServer"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de personnalisation, Section Connect](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Fichier de personnalisation, Section SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Fichier de personnalisation, Section UserList](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personnalisation de DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Paramètres Client requis](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Présentation du fichier de personnalisation](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Écriture d’un gestionnaire personnalisé](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)

