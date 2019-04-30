---
title: Objet d’erreur | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error
helpviewer_keywords:
- error object [ADO]
ms.assetid: a175d453-fa55-4f49-9ede-a26d83177919
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea282362853ca25a761f870970a288585a00160e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63275903"
---
# <a name="error-object"></a>Error, objet
Contient des détails sur les erreurs d’accès aux données qui se rapportent à une seule opération impliquant le fournisseur.  
  
## <a name="remarks"></a>Notes  
 Toute opération impliquant des objets ADO peut générer une ou plusieurs erreurs de fournisseur. Lorsqu’une erreur survient, un ou plusieurs **erreur** objets sont placés dans le [erreurs](../../../ado/reference/ado-api/errors-collection-ado.md) collection de la [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet. Lorsqu’une autre opération ADO génère une erreur, le **erreurs** collection est désactivée et le nouvel ensemble de **erreur** objets est placé dans le **erreurs** collection.  
  
> [!NOTE]
>  Chaque **erreur** objet représente une erreur de fournisseur spécifique, et non une erreur ADO. Erreurs ADO sont exposées au mécanisme de gestion des exceptions runtime. Par exemple, dans Microsoft Visual Basic, l’occurrence d’une erreur ADO spécifique déclenchera un **en cas d’erreur** événement et s’affichent dans le **erreur** objet. Pour obtenir une liste complète des erreurs ADO, consultez le [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) rubrique.  
  
 Vous pouvez lire un **erreur** des propriétés de l’objet pour obtenir des détails spécifiques sur chaque erreur, y compris les éléments suivants :  
  
-   Le [Description](../../../ado/reference/ado-api/description-property.md) propriété, qui contienne le texte de l’erreur. Il s’agit de la propriété par défaut.  
  
-   Le [nombre](../../../ado/reference/ado-api/number-property-ado.md) propriété, qui contient le **Long** valeur entière de la constante d’erreur.  
  
-   Le [Source](../../../ado/reference/ado-api/source-property-ado-error.md) propriété, qui identifie l’objet qui a déclenché l’erreur. Cela est particulièrement utile lorsque vous avez plusieurs **erreur** des objets dans le **erreurs** collection suite à une demande à une source de données.  
  
-   Le [SQLState](../../../ado/reference/ado-api/sqlstate-property.md) et [NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md) propriétés, qui fournissent des informations à partir de sources de données SQL.  
  
 En cas d’erreur de fournisseur, il est placé dans le **erreurs** collection de la **connexion** objet. ADO prend en charge le retour de plusieurs erreurs en une seule opération ADO pour des informations d’erreur spécifiques au fournisseur. Pour obtenir ces informations d’erreur complètes dans un gestionnaire d’erreurs, utilisez les fonctionnalités de récupération d’erreur appropriées de la langue ou l’environnement que vous travaillez, puis utiliser des boucles imbriquées pour énumérer les propriétés de chaque **erreur** de l’objet dans le **Erreurs** collection.  
  
> [!NOTE]
>  **Microsoft Visual Basic et les utilisateurs de VBScript** si il n’est pas valide **connexion** de l’objet, vous devez récupérer les informations d’erreur à partir de la **erreur** objet.  
  
 Tout comme les fournisseurs de faire, ADO efface le **OLE Error Info** avant d’effectuer un appel susceptible de générer une nouvelle erreur de fournisseur de l’objet. Toutefois, le **erreurs** collection sur le **connexion** objet est effacé et est rempli uniquement lorsque le fournisseur génère une nouvelle erreur ou lorsque le [clair](../../../ado/reference/ado-api/clear-method-ado.md) méthode est appelée.  
  
 Certaines propriétés et méthodes retournent des avertissements qui apparaissent sous la forme **erreur** des objets dans le **erreurs** collection sans pour autant arrêter l’exécution d’un programme. Avant d’appeler le [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), ou [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) méthodes sur un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet ; la [ouvrir](../../../ado/reference/ado-api/open-method-ado-connection.md) méthode sur un **connexion** objet ; ou définissez le [filtre](../../../ado/reference/ado-api/filter-property.md) propriété sur un **Recordset** d’objet, appelez le **effacer**(méthode) sur le **erreurs** collection. De cette façon, vous pouvez lire le [nombre](../../../ado/reference/ado-api/count-property-ado.md) propriété de la **erreurs** collection pour tester les avertissements retournés.  
  
 Le **erreur** objet n’est pas sécurisé pour le script.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de l’objet Error](../../../ado/reference/ado-api/error-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, NativeError, nombre, Source et SQLState, propriétés-exemple (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, nombre, Source et SQLState, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Objet Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Collection d’erreurs (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Annexe a : fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md)
