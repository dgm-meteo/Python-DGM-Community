# Python-DGM-Community
This repository is a shared framework for the DGM python community. A brief description of the main shared python notebooks will be detailed here.

# Script : **SpacePlot-v3-for-both-linux-windows.ipynb**

        Pour utiliser la fonction plotUsingRectangularMask, on commence par préparer les données :
        1- lecture des points particuliers à ploter sur la carte: 
            # Ces points sont lues dans un fichier csv 
            # contenant les colonnes suivantes : LON, LAT, NOM

        2- Sélection de la zone d'affichage:
            #     La zone d'affichage est sélectionnée par la variable "case" :
            #      case=1 # tout le maroc
            #      case=2 # un polygone définis par une liste de points
            #      case=3 # une région donnée par son numéro "reg"
            #         Liste des régions (extrait du shipfile) :
            #         ------------------------------------
            #         0            RABAT-SALÉ-ZEMMOUR-ZAER          
            #         1               RÉGION DE L'ORIENTAL           
            #         2              OUED EDDAHAB-LAGOUIRA           
            #         3                       FÈS-BOULMANE       
            #         4                  CHAOUIA OUARDIGHA        
            #         5         MARRAKECH-TENSIFT-EL HAOUZ 
            #         6                       TADLA-AZILAL   
            #         7           GHARB-CHRARDA-BÉNI HSSEN    
            #         8   LAÂYOUNE-BOUJDOUR-SAKIA EL HAMRA   
            #         9            TAZA-AL HOCEIMA-TOUNATE    
            #         10                  GRAND CASABLANCA   
            #         11                  MEKNÈS-TAFILALET 
            #         12                  SOUSS-MASSA-DRÂA  
            #         13                    TANGER-TÉTOUAN   
            #         14                 GUELMIM-ES-SEMARA  
            #         15                     DOUKKALA ABDA  

        3- Lecture des champs et préparation des informations d'entrée :
            # Les champs peuvent être lus à partir de :
            #    - fichier texte en utilisant la fonction (readMultiFieldsFromText)
            #    - fichier csv   en utilisant la fonction (readFieldsFromcsv)
            #    - fichier grib  en utilisant la fonction (readFieldsFromGribByNum)
            # On adapte les champs (cas par cas) au plot (par exemple, on convert la température en °C, le vent en
            # noeuds 'Knots', ...).
            #
            # Les entrées de la fonction plotUsingRectangularMask qui seront préparées à cette phase sont :
            #     X : tableau des tableaux 2D des coordonnées lon
            #     Y : tableau des tableaux 2D des coordonnées lat
            #     Z : tableau des tableaux 2D des valeurs des paramètres
            #     P : tableau des noms de paramètres
            #     steps  : tableau des pas de tracé des champs
            #     cmaps  : tableau des couleurs de tracé
            #     ptypes : tableau des type de tracé (contour, contourf, barbs, [arrow])
            # 
            # N.B: On ne peut tracer qu'une seule variable de type contourf. Si l'on en passe plusieurs à 
            # la fonction, uniquement la dernière qui apparaitra sur la carte.
            #
            # L'ordre des variables à tracer n'est pas important. 
            # La fonction trace tout d'abord la variable en contourf, puis les variables en contour 
            # et enfin les variables en barbules en utilisant des 'zorder' différents pour chacun des types de
            # plot.
        4-  Appeler la fonction plotUsingRectangularMask:
            # Pour le choix des couleurs, soit on ultilise les cmap prédéfinis de matplotlib ou ou on en 
            # construit un.
            # Pour avoir une idée des couleurs prédéfinis, executer la fonction showPredefinedCmap().
            #
            # Les cmap prédéfinis (par catégorie) sont : 
            # 'Perceptually Uniform Sequential':
            #             ['viridis', 'plasma', 'inferno', 'magma', 'cividis']
            # 'Sequential':
            #             ['Greys', 'Purples', 'Blues', 'Greens', 'Oranges', 'Reds',
            #              'YlOrBr', 'YlOrRd', 'OrRd', 'PuRd', 'RdPu', 'BuPu',
            #              'GnBu', 'PuBu', 'YlGnBu', 'PuBuGn', 'BuGn', 'YlGn']
            # 'Sequential (2)':
            #             ['binary', 'gist_yarg', 'gist_gray', 'gray', 'bone',
            #              'pink', 'spring', 'summer', 'autumn', 'winter', 'cool',
            #              'Wistia', 'hot', 'afmhot', 'gist_heat', 'copper']
            # 'Diverging':
            #             ['PiYG', 'PRGn', 'BrBG', 'PuOr', 'RdGy', 'RdBu', 'RdYlBu',
            #              'RdYlGn', 'Spectral', 'coolwarm', 'bwr', 'seismic']
            # 'Cyclic': 
            #             ['twilight', 'twilight_shifted', 'hsv']
            # 'Qualitative':
            #             ['Pastel1', 'Pastel2', 'Paired', 'Accent', 'Dark2',
            #              'Set1', 'Set2', 'Set3', 'tab10', 'tab20', 'tab20b',
            #              'tab20c']
            # 'Miscellaneous':
            #             ['flag', 'prism', 'ocean', 'gist_earth', 'terrain',
            #              'gist_stern', 'gnuplot', 'gnuplot2', 'CMRmap',
            #              'cubehelix', 'brg', 'gist_rainbow', 'rainbow', 'jet',
            #              'turbo', 'nipy_spectral', 'gist_ncar']
            #
            # Pour travailler avec le cmap inversé (couleur min correspondant à valeur max ainsi de suite), on
            # ajoute au nom le suffixe '_r', par exemple pour 'gray' le cmap inverse est 'gray_r'
            #

