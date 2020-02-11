---
title: Méthode Execute21 (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Execute21 method [RDS]
ms.assetid: 9f131c8d-1497-416d-8209-abb481c38f7b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8434345dcc4436865e4981a19ef1164d35a852f9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964200"
---
# <a name="execute21-method-rds"></a>Execute21, méthode (RDS)
Exécute la demande et crée un jeu d’enregistrements ADO à utiliser dans ADO 2,1.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.Execute21(ConnectionString As String, HandlerString As String, QueryString As String, lMarshalOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ConnectionString*  
 Chaîne utilisée pour se connecter au fournisseur OLE DB dans lequel la demande sera envoyée pour exécution. Si un gestionnaire est spécifié à l’aide de *HandlerString*, il peut modifier ou remplacer la chaîne de connexion.  
  
 *HandlerString*  
 La chaîne identifie le gestionnaire à utiliser avec cette exécution. La chaîne contient deux parties. La première partie contient le nom (ProgID) du gestionnaire à utiliser. La deuxième partie de la chaîne contient des arguments à passer au gestionnaire. La façon dont la chaîne d’arguments est interprétée est spécifique au gestionnaire. Les deux parties sont séparées par la première instance d’une virgule dans la chaîne (même si la chaîne d’arguments peut contenir des virgules supplémentaires). Les arguments sont facultatifs.  
  
 *QueryString*  
 Commande dans le langage de commande prise en charge par le fournisseur de OLE DB identifié dans la chaîne de connexion. Pour les fournisseurs basés sur SQL, il peut contenir [!INCLUDE[tsql](../../../includes/tsql-md.md)] une instruction Command, mais pour les fournisseurs non-SQL (par exemple, MSDataShape) il ne s' [!INCLUDE[tsql](../../../includes/tsql-md.md)] agit pas d’une instruction de requête.  
  
 En outre, si un gestionnaire est utilisé (et qu’il est fortement recommandé d’utiliser un gestionnaire), le gestionnaire peut modifier ou remplacer la valeur spécifiée ici. Par exemple, le gestionnaire remplace généralement *QueryString* par une chaîne de requête de son fichier. ini. Par défaut, le fichier Msdfmap. ini est utilisé.  
  
 *lMarshalOptions*  
 Utilisé pour définir les options de marshaling sur l’ensemble de lignes/Recordset retourné.  
  
 *TableID*  
 Variante de type VT_EMPTY ou VT_BSTR. Si cette valeur est de type VT_EMPTY, elle est ignorée. S’il est de type VT_BSTR, le jeu d’enregistrements est créé à l’aide de **adCmdTableDirect** en utilisant la valeur spécifiée ici et le paramètre *QueryString* est ignoré.  
  
 *lExecuteOptions*  
 Masque de masque des options d’exécution :  
  
 1 =*ReadOnly* l’objet Recordset sera ouvert à l’aide de **adLockReadOnly**.  
  
 2 =*Nobatch* , le jeu d’enregistrements est ouvert à l’aide de **adLockOptimistic**.  
  
 4 =*AllParamInfoSupplied* l’appelant garantit que les informations de paramètre pour tous les paramètres sont fournies dans *pParameters*.  
  
 8 = les informations de paramètres de*GetInfo* pour la requête seront obtenues à partir du fournisseur OLE DB et retournées dans le paramètre *pParameters* . La requête n’est pas exécutée et aucun Recordset n’est retourné.  
  
 16 = GetHiddenColumns l’objet Recordset est ouvert à l’aide de **adLockBatchOptimistic** et toutes les colonnes masquées sont incluses dans le Recordset.  
  
 Bien que *ReadOnly*, *nobatch* et *GetHiddenColumns* soient des options mutuellement exclusives, il ne s’agit pas d’une erreur pour en définir plusieurs. Si plusieurs options sont définies, *GetHiddenColumns* est prioritaire sur toutes les autres options, suivies de *ReadOnly*. Si aucune option n’est spécifiée, par défaut, le jeu d’enregistrements est ouvert à l’aide de la valeur **adLockBatchOptimistic** , mais les colonnes masquées ne sont pas incluses dans le jeu d’enregistrements.  
  
 *pParameters*  
 Variant qui contient un tableau sécurisé de définitions de paramètres. Si l’option *GetInfo* a été spécifiée dans *lExecuteOptions*, ce paramètre est utilisé pour retourner les définitions de paramètres obtenues à partir du fournisseur OLE DB. Dans le cas contraire, ce paramètre peut être vide.  
  
## <a name="remarks"></a>Notes  
 Le paramètre *HandlerString* peut avoir la valeur null. Ce qui se produit dans ce cas dépend de la configuration du serveur RDS. La chaîne de gestionnaire « MSDFMAP. Handler » indique que le gestionnaire fourni par Microsoft (msdfmap. dll) doit être utilisé. Une chaîne de gestionnaire « MASDFMAP. Handler, Sample. ini » indique que le gestionnaire msdfmap. dll doit être utilisé et que l’argument « Sample. ini » doit être passé au gestionnaire. MSDFMAP. dll interprète l’argument comme une direction pour utiliser le fichier Sample. ini afin de vérifier la connexion et les chaînes de requête.  
  
> [!NOTE]
>  La méthode **Execute21** est une version de la [méthode Execute (RDS)](../../../ado/reference/rds-api/execute-method-rds.md). Lorsque vous devez utiliser la méthode **Execute** pour communiquer avec ADO 2,1, la méthode **Execute21** peut être appelée à la place. Les fonctionnalités de la méthode **Execute** dans ADO 2,5 et versions ultérieures sont un sur-ensemble des fonctionnalités fournies pour la même méthode dans ADO 2,1.  
  
## <a name="applies-to"></a>S'applique à  
 [DataFactory, objet (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


