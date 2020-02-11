---
title: Paramètres client requis | Microsoft Docs
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
ms.openlocfilehash: bdb99cb3d792900f48ceb69c25c7ae720c339683
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922290"
---
# <a name="required-client-settings"></a>Paramètres client obligatoires
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Spécifiez les paramètres suivants pour utiliser un gestionnaire **DataFactory** personnalisé.  
  
-   Spécifiez « Provider = MS Remote » dans la propriété de la propriété du [fournisseur](../../../ado/reference/ado-api/provider-property-ado.md) d’objets de [connexion (](../../../ado/reference/ado-api/connection-object-ado.md) ADO) ou la chaîne de connexion de l’objet de **connexion** «**Provider**= ».  
  
-   Affectez à la propriété [CursorLocation (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md) la valeur **adUseClient**.  
  
-   Spécifiez le nom du gestionnaire à utiliser dans la propriété du **Gestionnaire** de l’objet [DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md) ou le mot clé de la chaîne de connexion de l’objet [Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) «**handler**= ». (Vous ne pouvez pas définir le gestionnaire dans la chaîne de connexion de l’objet de **connexion** .)  
  
 Les services Bureau à distance fournissent un gestionnaire par défaut sur le serveur nommé **msdfmap. Gestionnaire**. (Le fichier de personnalisation par défaut est nommé MSDFMAP. INI.)  
  
 **Exemple**  
  
 Supposons que les sections suivantes dans le **msdfmap. INI** et le nom de la source de données, AdvWorks, ont été définis précédemment :  
  
```console
[connect CustomerDataBase]  
Access=ReadWrite  
Connect="DSN=AdvWorks"  
  
[sql CustomerById]  
SQL="SELECT * FROM Customers WHERE CustomerID = ?"  
```  
  
 Les extraits de code suivants sont écrits en Visual Basic :  
  
## <a name="rdsdatacontrol-version"></a>Licence. Version de DataControl  
  
```vb
Dim dc as New RDS.DataControl  
Set dc.Handler = "MSDFMAP.Handler"  
Set dc.Server = "https://yourServer"  
Set dc.Connect = "Data Source=CustomerDatabase"  
Set dc.SQL = "CustomerById(4)"  
dc.Refresh  
```  
  
## <a name="recordset-version"></a>Version de l’ensemble d’enregistrements  
  
```vb
Dim rs as New ADODB.Recordset  
rs.CursorLocation = adUseClient  
```  
  
 Spécifiez la propriété ou le mot clé de la [propriété du gestionnaire (RDS)](../../../ado/reference/rds-api/handler-property-rds.md) . la propriété ou le mot clé de la [propriété Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) ; et les identificateurs *CustomerByID* et *CustomerDatabase* . Ouvrez ensuite l’objet **Recordset**  
  
 rs.Open "CustomerById(4)", "Handler=MSDFMAP.Handler;" & _  
  
```vb
"Provider=MS Remote;Data Source=CustomerDatabase;" & _  
"Remote Server=https://yourServer"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Section de connexion au fichier de personnalisation](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Section SQL du fichier de personnalisation](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Section UserList du fichier de personnalisation](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personnalisation de DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Paramètres client requis](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Fonctionnement du fichier de personnalisation](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Écriture d’un gestionnaire personnalisé](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)

