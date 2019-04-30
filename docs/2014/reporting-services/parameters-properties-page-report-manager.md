---
title: Page de propriétés de paramètres (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: ebb53598-2378-46ae-8935-d5192f8ea49a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f83e66d238aa67b28bf547540c5a6b5dfcc9c92d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188290"
---
# <a name="parameters-properties-page-report-manager"></a>Page de propriétés des paramètres (Gestionnaire de rapports)
  La page de propriétés des paramètres vous permet d'afficher ou de modifier les paramètres d'un rapport paramétrable.  
  
 Les paramètres sont spécifiés dans la définition de rapport avant la publication du rapport. Une fois le rapport publié, vous pouvez modifier certaines valeurs de propriétés des paramètres. Les valeurs que vous pouvez modifier varient suivant la définition des paramètres dans le rapport. Par exemple, si une liste de valeurs statiques est définie pour un paramètre, vous pouvez choisir une autre valeur statique à utiliser par défaut, mais vous ne pouvez ni ajouter ni supprimer des valeurs de la liste. De la même façon, si le paramètre est basé sur une requête, tous les aspects de cette requête (notamment le dataset utilisé, l'autorisation d'utiliser ou non des valeurs Null ou vides, et la fourniture d'une valeur par défaut) sont définis dans le rapport avant sa publication.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-parameters-properties-page"></a>Pour ouvrir la page de propriétés Paramètres  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le rapport pour lequel vous souhaitez modifier des paramètres.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page des propriétés générales pour le rapport s'ouvre.  
  
4.  Sélectionnez l'onglet **Paramètres** . Si l'onglet **Paramètres** n'est pas visible, cela signifie que le rapport ne contient aucun paramètre.  
  
## <a name="options"></a>Options  
 **Nom du paramètre**  
 Spécifie le nom du paramètre.  
  
 **Type de données**  
 Spécifie le type de données du paramètre.  
  
 **A la valeur par défaut**  
 Activez cette case à cocher si le paramètre possède une valeur par défaut. L'activation de cette case à cocher entraîne celle de la case à cocher **Valeur par défaut**. Elle active également **Null** si le paramètre de rapport accepte les valeurs Null. Si l'option **Possède une valeur par défaut** n'est pas sélectionnée, vous devez masquer la valeur ou inviter l'utilisateur à fournir une valeur lorsque le rapport s'exécute.  
  
 **Valeur par défaut**  
 Spécifie une valeur pour le paramètre. Pour spécifier une valeur par défaut, la case à cocher **Possède une valeur par défaut** doit être activée et la case à cocher **Null** désactivée. Une valeur par défaut peut être fournie par la définition de rapport. Si l'option **Valeur par défaut** est peuplée d'une ou de plusieurs valeurs statiques, ces valeurs proviennent du rapport. Si l'option **Valeur par défaut** est **Basée sur une requête**, la valeur de paramètre est déterminée par une requête qui est définie dans le rapport.  
  
 Si l'option **Valeur par défaut** accepte une valeur, vous pouvez taper une constante ou une syntaxe valide pour l'extension de traitement des données utilisée avec le rapport. Par exemple, si le langage de requête de l'extension pour le traitement des données prend en charge les caractères génériques, vous pouvez spécifier un caractère générique en tant que valeur par défaut.  
  
 Si vous spécifiez ultérieurement qu'une invite doit être affichée, la valeur par défaut devient une valeur initiale que les utilisateurs peuvent utiliser ou modifier. Si vous ne demandez pas une valeur de paramètre, cette valeur est utilisée pour tous les utilisateurs qui exécutent le rapport.  
  
 **Null**  
 Activez cette case à cocher pour spécifier comme Null la valeur par défaut. Une valeur Null signifie que le rapport s'exécute même si l'utilisateur ne fournit pas de valeur de paramètre. Si cette colonne ne contient aucune case à cocher, cela signifie que le paramètre n'accepte pas les valeurs Null.  
  
 **Hide**  
 Activez cette case à cocher pour masquer le paramètre dans la zone de paramètres qui s'affiche dans la partie supérieure du rapport. Ce paramètre apparaît toujours dans les pages de définition d'abonnement et peut toujours être spécifié dans l'URL d'un rapport. Il est utile de masquer ce paramètre si vous souhaitez que le rapport soit toujours exécuté avec une valeur par défaut que vous spécifiez.  
  
 Désactivez cette case à cocher si vous souhaitez afficher le paramètre dans le rapport.  
  
 **Inviter l’utilisateur**  
 Activez cette case à cocher pour afficher une zone de texte qui demande aux utilisateurs de fournir une valeur de paramètre.  
  
 Désactivez cette case à cocher si vous souhaitez exécuter le rapport en mode sans assistance (par exemple, pour générer des instantanés d'historique de rapport ou d'exécution de rapport), si vous souhaitez utiliser la même valeur de paramètre pour tous les utilisateurs ou si vous n'avez pas besoin d'une entrée utilisateur pour cette valeur.  
  
 **Texte affiché**  
 Fournit une chaîne de texte qui apparaît en regard de la zone de texte du paramètre. La chaîne contient une étiquette ou une description. Aucune limite n'est imposée quant à la longueur de chaîne. Les chaînes de texte plus longues sont renvoyées à la ligne dans l'espace fourni.  
  
## <a name="see-also"></a>Voir aussi  
 [Page Propriétés générales, Rapports &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md)   
 [Aide (F1) du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
