# Creación de Web Estática con Jekyll

## Requisitos previos:
  ### Instalación de paquetes:
 ´´´sh
  sudo apt-get install ruby-full build-essential zlib1g-dev
```

  ## Inclusión de variables de Ruby:
    echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
    echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
    echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc
  ## Instalación de jekyll:
    gem install jekyll bundler
 
  ## Debes crear un sitio con el nombre que elijas:
    jekyll new nombre_sitio
    cd nombre_sitio
  ## Puesta en marcha
    bundle exec jekyll serve
    
   ## Para probarlo desde el navegador:
      localhost:4000
