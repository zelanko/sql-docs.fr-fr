---
title: Execute21, méthode (RDS) | Microsoft Docs
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
manager: jroth
ms.openlocfilehash: 1c65fe01fef6ba2cab2f41ca056bb96a8ef50f39
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66707858"
---
# <a name="execute21-method-rds"></a>Execute21, méthode (RDS)
Exécute la requête et crée un objet recordset ADO pour une utilisation dans ADO 2.1.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.Execute21(ConnectionString As String, HandlerString As String, QueryString As String, lMarshalOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ConnectionString*  
 Chaîne utilisée pour se connecter au fournisseur OLE DB où la demande sera envoyée pour exécution. Si un gestionnaire est spécifié à l’aide de *HandlerString*, il peut modifier ou remplacer la chaîne de connexion.  
  
 *HandlerString*  
 La chaîne identifie le gestionnaire à utiliser avec cette exécution. La chaîne contient deux parties. La première partie contient le nom (ProgID) du gestionnaire à utiliser. La deuxième partie de la chaîne contient des arguments à passer au gestionnaire. Interprétation de la chaîne d’arguments est gestionnaire spécifique. Les deux parties sont séparées par la première instance d’une virgule dans la chaîne (bien que la chaîne d’arguments pouvant contenir des virgules supplémentaires). Les arguments sont facultatifs.  
  
 *QueryString*  
 Une commande dans le langage de commande pris en charge par le fournisseur OLE DB identifié dans la chaîne de connexion. Pour les fournisseurs SQL, il peut contenir un [!INCLUDE[tsql](../../../includes/tsql-md.md)] instruction de commande, mais pour les fournisseurs non-SQL (par exemple, MSDataShape) peut différer un [!INCLUDE[tsql](../../../includes/tsql-md.md)] instruction de requête.  
  
 En outre, si un gestionnaire est utilisé (et il est fortement recommandé d’utiliser qu’un gestionnaire), le gestionnaire peut alter ou remplacez la valeur spécifiée ici. Par exemple, le gestionnaire remplace généralement *QueryString* avec une chaîne de requête à partir de son fichier .ini. Par défaut, le fichier Msdfmap.ini est utilisé.  
  
 *lMarshalOptions*  
 Utilisé pour définir les options de marshaling sur l’ensemble de lignes/jeu d’enregistrements retournés.  
  
 *TableID*  
 Un variant de type VT_EMPTY ou VT_BSTR. Si cette valeur est de type VT_EMPTY, il est ignoré. Si elle est de type VT_BSTR, le jeu d’enregistrements est créé à l’aide de **adCmdTableDirect** à l’aide de la valeur spécifiée ici et *QueryString* paramètre est ignoré.  
  
 *lExecuteOptions*  
 Un masque de bits des options d’exécution :  
  
 1 =*ReadOnly* le recordset est ouvert à l’aide de **adLockReadOnly**.  
  
 2 =*NoBatch* le recordset est ouvert à l’aide de **adLockOptimistic**.  
  
 4 =*AllParamInfoSupplied* l’appelant garantit que les informations de paramètre pour tous les paramètres sont fournies dans *pParameters*.  
  
 8 =*GetInfo* informations de paramètre pour la requête seront obtenues à partir du fournisseur OLE DB et retournées dans le *pParameters* paramètre. La requête n’est pas exécutée et aucun jeu d’enregistrements n’est retournée.  
  
 16 = GetHiddenColumns le recordset est ouvert à l’aide de **adLockBatchOptimistic** et les colonnes masquées seront inclus dans le jeu d’enregistrements.  
  
 Bien que *ReadOnly*, *NoBatch* et *GetHiddenColumns* sont des options mutuellement exclusives, il n’est pas une erreur pour définir plusieurs fois. Si plusieurs options sont définies, *GetHiddenColumns* est prioritaire sur toutes les autres options, suivies de *ReadOnly*. Si aucune option est spécifiée, par défaut, le jeu d’enregistrements est ouvert en utilisant **adLockBatchOptimistic** mais les colonnes masquées ne sont pas inclus dans le jeu d’enregistrements.  
  
 *pParameters*  
 Variant qui contient un tableau sécurisé de définitions de paramètres. Si le *GetInfo* option a été spécifiée dans *lExecuteOptions*, ce paramètre est utilisé pour retourner les définitions de paramètres obtenues à partir du fournisseur OLE DB. Sinon, ce paramètre peut être vide.  
  
## <a name="remarks"></a>Notes  
 Le *HandlerString* paramètre peut être null. Ce qui se produit dans ce cas dépend de la façon dont le serveur de services Bureau à distance est configuré. Une chaîne de gestionnaire de « MSDFMAP.handler » indique que le gestionnaire fourni par Microsoft (Msdfmap.dll) doit être utilisé. Une chaîne de gestionnaire de « MASDFMAP.handler,sample.ini » indique que le Gestionnaire de Msdfmap.dll doit être utilisé et que l’argument « sample.ini » doit être passé au gestionnaire. MSDFMAP.dll interprétera l’argument comme une direction à utiliser le sample.ini pour vérifier les chaînes de connexion et la requête.  
  
> [!NOTE]
>  Le **Execute21** méthode est une version de la [Execute, méthode (RDS)](../../../ado/reference/rds-api/execute-method-rds.md). Où vous devez utiliser le **Execute** méthode pour communiquer avec ADO 2.1, le **Execute21** méthode peut être appelée à la place. Les fonctionnalités de la **Execute** méthode dans ADO 2.5 et versions ultérieur sont un sur-ensemble de fonctionnalités de la même méthode dans ADO 2.1.  
  
## <a name="applies-to"></a>S'applique à  
 [DataFactory, objet (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


