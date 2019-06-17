---
title: Commentaires sur HelloData | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hellodata sample application [ADO]
ms.assetid: a2831d77-7040-4b73-bbae-fe0bf78107ed
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 23ba7235ddd8ea05b7217c88bc76e7bfe50bbd98
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702389"
---
# <a name="comments-on-hellodata"></a>Commentaires sur HelloData
Étapes de l’application HelloData via les opérations de base d’une application ADO typique : obtention, examen, la modification et la mise à jour des données. Lorsque vous démarrez l’application, cliquez sur le premier bouton, **obtenir des données**. Cela exécutera le **GetData** sous-routine.  
  
## <a name="getdata"></a>GetData  
 **GetData** place une chaîne de connexion valide dans une variable au niveau du module, *m_sConnStr*. Pour plus d’informations sur les chaînes de connexion, consultez [création de la chaîne de connexion](../../../ado/guide/data/creating-a-connection-string.md).  
  
 Affecter un gestionnaire d’erreurs à l’aide de Visual Basic **OnError** instruction. Pour plus d’informations sur la gestion des erreurs dans ADO, consultez [gestion des erreurs](../../../ado/guide/data/error-handling.md). Un nouveau **connexion** objet est créé et le **CursorLocation** propriété est définie sur **adUseClient** , car l’exemple HelloData crée un  *jeu d’enregistrements déconnecté*. Cela signifie que, dès que les données ont été récupérées à partir de la source de données, la connexion physique avec la source de données est interrompue, mais vous pouvez continuer à utiliser avec les données mises en cache localement dans votre **Recordset** objet.  
  
 Une fois que la connexion a été ouvert, affecter une chaîne SQL à une variable (sSQL). Puis créez une instance d’un nouveau **Recordset** objet, `m_oRecordset1`. Dans la ligne suivante de code, ouvrez le **Recordset** existant **connexion**, en passant dans `sSQL` comme source de la **Recordset**. Vous aider à ADO à déterminer que le code SQL de chaîne vous ont réussi comme source pour le **Recordset** est une définition textuelle d’une commande en passant **adCmdText** dans l’argument final vers le **Jeu d’enregistrements ouvert** (méthode). Cette ligne définit également la **LockType** et **CursorType** associé à la **Recordset**.  
  
 La ligne suivante du code définit le **MarshalOptions** propriété égale à **adMarshalModifiedOnly**. **MarshalOptions** indique les enregistrements qui doivent être marshalées vers la couche intermédiaire (ou un serveur Web). Pour plus d’informations sur le marshaling, consultez la documentation de COM. Lorsque vous utilisez **adMarshalModifiedOnly** avec un curseur côté client ([CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) = **adUseClient**), seuls les enregistrements qui ont été modifiés sur le client mis à jour dans la couche intermédiaire. Paramètre **MarshalOptions** à **adMarshalModifiedOnly** peut améliorer les performances, car moins de lignes sont marshalés.  
  
 Ensuite, déconnectez le **Recordset** en définissant son **ActiveConnection** propriété égale à **rien**. Pour plus d’informations, consultez la section « Déconnexion et reconnexion le jeu d’enregistrements » dans [mise à jour et persistance des données](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Fermez la connexion à la source de données et de détruire existant **connexion** objet. Cela libère les ressources qu’il utilise.  
  
 L’étape finale consiste à définir le **Recordset** en tant que le **DataSource** pour la grille de données Microsoft contrôle sur le formulaire par conséquent, que vous pouvez facilement afficher les données à partir de la **Recordset** sur le formulaire.  
  
 Cliquez sur le deuxième bouton, **examiner les données**. Cette commande exécute le **ExamineData** sous-routine.  
  
## <a name="examinedata"></a>ExamineData  
 ExamineData utilise plusieurs méthodes et propriétés de la **Recordset** objet pour afficher des informations sur les données dans le **Recordset**. Il signale le nombre d’enregistrements à l’aide de la **RecordCount** propriété. Il effectue une itération sur la **Recordset** et imprime la valeur de la **AbsolutePosition** propriété dans la zone de texte d’affichage sur le formulaire. Lorsque vous êtes également dans la boucle, la valeur de la **signet** propriété pour le troisième enregistrement est placée dans une variable de type variante, *vBookmark*, pour une utilisation ultérieure.  
  
 La routine revient directement à l’enregistrement de tiers à l’aide de la variable de signet stockées précédemment. Les appels de routine le **WalkFields** sous-routine, qui effectue une itération sur la **champs** collection de la **Recordset** et affiche les détails de chaque **champ**  dans la collection.  
  
 Enfin, **ExamineData** utilise le **filtre** propriété de la **Recordset** à l’écran pour que les enregistrements avec un **CategoryId** égal à 2. Le résultat de l’application de ce filtre est immédiatement visible dans la grille d’affichage sur le formulaire.  
  
 Pour plus d’informations sur la fonctionnalité de la **ExamineData** sous-routine, consultez [examen des données](../../../ado/guide/data/examining-data.md).  
  
 Ensuite, cliquez sur le troisième bouton **modifier les données**. Cela exécutera le **EditData** sous-routine.  
  
## <a name="editdata"></a>EditData  
 Lorsque le code entre la **EditData** sous-routine, le **Recordset** est toujours filtrée sur **CategoryId** égal à 2, afin que seuls les éléments qui répondent aux critères de filtre sont visible. Il parcourt tout d’abord le **Recordset** et augmente le prix de chaque élément visible dans le **Recordset** de 10 %. La valeur de la **prix** champ est modifié en définissant le **valeur** propriété pour ce champ est égal à un nouveau montant valide.  
  
 N’oubliez pas que le **Recordset** est déconnecté de la source de données. Les modifications qui ont été apportées dans **EditData** sont effectuées uniquement à la copie mise en cache localement des données. Pour plus d’informations, consultez [modification des données](../../../ado/guide/data/editing-data.md).  
  
 Les modifications ne sont pas effectuées sur la source de données jusqu'à ce que vous cliquez sur le quatrième bouton **données mises à jour**. Cela exécutera le **UpdateData** sous-routine.  
  
## <a name="updatedata"></a>UpdateData  
 UpdateData supprime tout d’abord le filtre a été appliqué à la **Recordset**. Le code supprime et réinitialise `m_oRecordset1` en tant que le **DataSource** pour Microsoft liée aux données sur le formulaire afin que le non filtrées **Recordset** apparaît dans la grille.  
  
 Le code vérifie ensuite si vous pouvez revenir en arrière le **Recordset** à l’aide de la **prend en charge** méthode avec le **adMovePrevious** argument.  
  
 La routine se déplace vers le premier enregistrement à l’aide du **MoveFirst** (méthode) et affiche les valeurs du champ d’origine et actuelles, à l’aide de la **OriginalValue** et **valeur** propriétés de la **champ** objet. Ces propriétés, avec le **UnderlyingValue** propriété (non utilisé ici), sont abordées dans [mise à jour et persistance des données](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Ensuite, une nouvelle **connexion** objet est créé et utilisé pour rétablir la connexion à la source de données. Vous vous reconnectez le **Recordset** à la source de données en définissant la nouvelle **connexion** en tant que le **ActiveConnection** pour le **Recordset**. Pour envoyer les mises à jour sur le serveur, le code appelle **UpdateBatch** sur le **Recordset**.  
  
 Si la mise à jour de lot réussit, une variable d’indicateur de module, `m_flgPriceUpdated`, est définie sur True. Cela vous rappellera ultérieurement de nettoyer toutes les modifications qui ont été apportées à la base de données.  
  
 Enfin, le code déplace le curseur vers le premier enregistrement dans le **Recordset** et affiche les valeurs d’origine et actuelles. Les valeurs sont identiques après l’appel à **UpdateBatch**.  
  
 Pour plus d’informations sur la façon de mettre à jour des données, y compris ce qu’il faut faire lorsque les données sur le serveur change lors de votre **Recordset** est déconnecté, consultez [mise à jour et persistance des données](../../../ado/guide/data/updating-and-persisting-data.md).  
  
## <a name="formunload"></a>Form_Unload  
 Le **Form_Unload** sous-routine est importante pour plusieurs raisons. Tout d’abord, car il s’agit d’un exemple d’application, Form_Unload nettoie les modifications qui ont été apportées à la base de données avant la fermeture de l’application. Ensuite, le code montre comment une commande peut être exécutée directement à partir d’une ouverture **connexion** objet à l’aide de la **Execute** (méthode). Enfin, il montre un exemple d’exécution d’une requête sans renvoi à la ligne (une requête de mise à jour) sur la source de données.
