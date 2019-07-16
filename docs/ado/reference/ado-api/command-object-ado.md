---
title: Command, objet (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command
helpviewer_keywords:
- Command object [ADO]
ms.assetid: a02c22fb-542d-465e-a629-30fd59dcbebf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bbce299e2e9f67b705f940480913c7d8ac367d0d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67919797"
---
# <a name="command-object-ado"></a>Command, objet (ADO)
Définit une commande spécifique que vous avez l’intention d’exécuter par rapport à une source de données.  
  
## <a name="remarks"></a>Notes  
 Utilisez un **commande** objet pour interroger une base de données et retourner des enregistrements dans une [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet, pour exécuter une opération en bloc ou pour manipuler la structure d’une base de données. Selon les fonctionnalités du fournisseur, certaines **commande** collections, méthodes ou propriétés peuvent générer une erreur lorsqu’elles sont référencées.  
  
 Avec les collections, les méthodes et les propriétés d’un **commande** de l’objet, vous pouvez procédez comme suit :  
  
-   Définir le texte exécutable de la commande (par exemple, une instruction SQL) avec la [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) propriété. Vous pouvez également pour la commande ou requête structures autres que de simples chaînes (par exemple, les requêtes de modèle XML) définissent la commande avec le [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) propriété.  
  
-   Si vous le souhaitez, indiquer le dialecte de commande utilisé dans le **CommandText** ou **CommandStream** avec la [dialecte](../../../ado/reference/ado-api/dialect-property.md) propriété.  
  
-   Définir des requêtes paramétrables ou les arguments de procédure stockée avec [paramètre](../../../ado/reference/ado-api/parameter-object.md) objets et le [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) collection.  
  
-   Indiquer si les noms de paramètre doivent être transmis au fournisseur avec le [NamedParameters](../../../ado/reference/ado-api/namedparameters-property-ado.md) propriété.  
  
-   Exécuter une commande et retourner un **Recordset** objet si nécessaire avec le [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) (méthode).  
  
-   Spécifiez le type de commande avec le [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) propriété avant l’exécution pour optimiser les performances.  
  
-   Vérifier si le fournisseur enregistre une version préparée (ou compilée) de la commande avant l’exécution avec le [Prepared](../../../ado/reference/ado-api/prepared-property-ado.md) propriété.  
  
-   Définir le nombre de secondes d’attente d’un fournisseur d’une commande à exécuter avec le [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md) propriété.  
  
-   Associer une connexion ouverte avec un **commande** objet en définissant son [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) propriété.  
  
-   Définir le [nom](../../../ado/reference/ado-api/name-property-ado.md) propriété pour identifier le **commande** objet en tant que méthode sur associé [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
-   Passer un **commande** de l’objet à la [Source](../../../ado/reference/ado-api/source-property-ado-recordset.md) propriété d’un **Recordset** pour obtenir des données.  
  
-   Accéder aux attributs spécifiques au fournisseur avec le [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection.  
  
> [!NOTE]
>  Pour exécuter une requête sans utiliser un **commande** d’objet, passez une chaîne de requête à la [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) méthode d’un **connexion** objet ou à la [ouvrir](../../../ado/reference/ado-api/open-method-ado-recordset.md)méthode d’un **Recordset** objet. Toutefois, un **commande** objet est requis lorsque vous souhaitez conserver le texte de commande et exécuter de nouveau ou utiliser des paramètres de requête.  
  
 Pour créer un **commande** objet indépendamment défini précédemment **connexion** de l’objet, définissez son **ActiveConnection** en une chaîne de connexion valide. ADO crée toujours un **connexion** objet, mais elle n’affecte pas cet objet à une variable objet. Toutefois, si vous associez plusieurs **commande** objets avec la même connexion, vous devez explicitement créer et ouvrir un **connexion** objet ; ce affecte le **connexion** objet à une variable objet. Vous assurer que le **connexion** objet a été ouverte avec succès avant de l’affecter à la **ActiveConnection** propriété de la **commande** de l’objet, car l’affectation d’un fermé **connexion** objet provoque une erreur. Si vous ne définissez pas la **ActiveConnection** propriété de la **commande** de l’objet à cette variable objet, ADO crée un nouveau **connexion** pour chaque objet  **Commande** de l’objet, même si vous utilisez la même chaîne de connexion.  
  
 Pour exécuter un **commande**, appelez-le son [nom](../../../ado/reference/ado-api/name-property-ado.md) propriété sur associé **connexion** objet. Le **commande** doit avoir son **ActiveConnection** propriété définie sur le **connexion** objet. Si le **commande** possède des paramètres, passez ses valeurs en tant qu’arguments à la méthode.  
  
 Si deux ou plusieurs **commande** les objets sont exécutés sur la même connexion et soit **commande** objet est une procédure stockée avec des paramètres de sortie, une erreur se produit. Pour exécuter chaque **commande** de l’objet, utiliser des connexions distinctes ou déconnectez tous les autres **commande** objets à partir de la connexion.  
  
 Le **paramètres** collection est le membre par défaut de la **commande** objet. Par conséquent, les deux instructions suivantes sont équivalentes.  
  
```  
objCmd.Parameters.Item(0)  
objCmd(0)  
```  
  
-   Le **commande** objet n’est pas sécurisé pour le script.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés de l’objet commande, méthodes et événements](../../../ado/reference/ado-api/command-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Collection de paramètres (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Collection de propriétés (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Annexe A : fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md)
