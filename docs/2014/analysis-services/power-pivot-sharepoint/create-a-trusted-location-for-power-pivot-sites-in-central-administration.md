---
title: Créer un emplacement approuvé pour les sites PowerPivot dans l’Administration centrale | Microsoft Docs
ms.custom: ''
ms.date: 04/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a666f365-cd93-43a3-9d3d-e429dfc19b66
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b54c06d86490c92936d147f2876d663f43d99fac
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66071591"
---
# <a name="create-a-trusted-location-for-powerpivot-sites-in-central-administration"></a>Créer un emplacement approuvé pour les sites PowerPivot dans l'Administration centrale
  Excel Services vous permet de spécifier les emplacements qui constituent des référentiels valides pour les classeurs que vous ouvrez sur un serveur SharePoint. Ces emplacements sont appelés « emplacements approuvés ». Vous pouvez utiliser des paramètres de configuration différents pour chaque emplacement approuvé créé. Pour un déploiement de PowerPivot pour SharePoint, vous envisagez peut être de créer un emplacement approuvé pour les sites qui contiennent des classeurs PowerPivot, pour pouvoir appliquer les paramètres les plus appropriés à l'accès aux données PowerPivot tout en conservant les paramètres par défaut pour le reste de la batterie.  
  
  
  
## <a name="prerequisites"></a>Prérequis  
 Vous devez être administrateur de service ou de batterie de serveurs pour désigner une URL comme emplacement approuvé.  
  
 Vous devez connaître l'adresse URL du site SharePoint contenant la Galerie PowerPivot ou une autre bibliothèque qui stocke vos classeurs. Pour obtenir l’adresse, ouvrez le site qui contient la bibliothèque, cliquez sur **galerie PowerPivot**, sélectionnez **propriétés**, puis copiez la première partie de l’adresse (URL) qui contient le nom du serveur et le site chemin d’accès.  
  
##  <a name="overview"></a> Vue d'ensemble  
 Une installation initiale d'Excel Services spécifie 'http://' comme son emplacement approuvé, ce qui signifie que les classeurs de n'importe quel site de la batterie peuvent être ouverts sur le serveur. Si vous avez besoin d'un contrôle plus strict sur les emplacements à considérer comme dignes de confiance, vous pouvez créer de nouveaux emplacements approuvés qui mappent à des sites spécifiques dans votre batterie, puis faire varier les paramètres et les autorisations pour chacun.  
  
 La création d'un emplacement approuvé pour les sites hébergeant des classeurs PowerPivot est particulièrement utile si vous voulez conserver les valeurs par défaut pour le reste de la batterie de serveurs, tout en appliquant des paramètres différents, plus appropriés pour l'accès aux données PowerPivot. Par exemple, un emplacement approuvé optimisé pour les classeurs PowerPivot peut disposer d'une taille maximale de classeur de 50 Mo, tandis que le reste de la batterie utilise la valeur par défaut de 10 Mo.  
  
 La création d'un emplacement approuvé est recommandée si vous utilisez des bibliothèques Galerie PowerPivot pour afficher un aperçu des classeurs publiés, et que des avertissements d'actualisation des données s'affichent au lieu de l'image d'aperçu que vous attendez. La Galerie PowerPivot restitue des images miniatures des rapports et classeurs à l'aide de données et d'informations de présentation dans le document. Si l'avertissement lors de l'actualisation des données est activé pour un emplacement approuvé, il est possible que la Galerie PowerPivot ne dispose pas d'autorisations suffisantes pour procéder à l'actualisation. Par conséquent, une erreur est générée à la place de l'image miniature. L'ajout d'un site contenant la Galerie PowerPivot comme nouvel emplacement approuvé permet d'éviter ce problème.  
  
##  <a name="create"></a> Créer un emplacement approuvé pour l’accès aux données PowerPivot  
  
1.  Dans l'Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur l'application de service Excel Services.  
  
3.  Cliquez sur **Emplacements de fichiers approuvés**.  
  
4.  Cliquez sur **Ajouter un emplacement de fichier approuvé**.  
  
5.  Entrez l'URL d'un site contenant une bibliothèque Galerie PowerPivot.  
  
6.  Dans Type d'emplacement, sélectionnez **Microsoft SharePoint Foundation**.  
  
    > [!IMPORTANT]  
    >  Les types d'emplacement UNC et HTTP ne sont pas pris en charge pour l'accès aux données PowerPivot.  
  
7.  Acceptez tous les paramètres par défaut pour les propriétés dans Gestion des sessions, Propriétés du classeur et Comportement du calcul.  
  
8.  Dans Propriétés du classeur, affectez à **Taille maximale du classeur** la valeur **50**. Cela aligne la limite supérieure de la taille des fichiers de classeurs sur la limite supérieure des téléchargements de fichiers vers l'application Web parente. Si la taille de vos classeurs est supérieure à 50 mégaoctets, vous devez augmenter encore plus la limite de la taille des fichiers. Pour plus d’informations, consultez [configurer une taille de téléchargement de fichier maximale &#40;PowerPivot pour SharePoint&#41;](configure-maximum-file-upload-size-power-pivot-for-sharepoint.md).  
  
9. Dans Données externes, vérifiez que l'option Autoriser les données externes a la valeur **Bibliothèques de connexions de données approuvées et incorporées**. Ce paramètre est requis pour l'accès aux données PowerPivot dans un classeur.  
  
10. De plus, dans Données externes, pour Avertir lors de l'actualisation, désactivez la case à cocher **Avertissement d'actualisation activé**. La désactivation de cette case à cocher permet à la Galerie PowerPivot d'ignorer les messages d'avertissement habituels et d'afficher des images d'aperçu d'un classeur à la place.  
  
11. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Galerie PowerPivot](../../2014-toc/books-online-for-sql-server-2014.md)   
 [Créer et personnaliser une galerie PowerPivot](create-and-customize-power-pivot-gallery.md)   
 [Utiliser la Galerie PowerPivot](use-power-pivot-gallery.md)  
  
  
