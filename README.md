# gcloud Configuration Auto Switcher

Juggling many gcloud configurations at a time can be problematic. This recently happend when I deployed the wrong code to the wrong configuration, taking a service runing for a city offline for a few minutes.

Solution

Create a .gcloudrc file with the name of your configuration

Example .gcloudrc

```
my-config-1
```

Then add this script to your ~/.zshrc

```bash
# gcloud config auto switcher

gcloud-config(){
  if [ -e  .gcloudrc ]
  then
    local config=`cat .gcloudrc`
    echo "Activating gcloud configuration $config"
    gcloud config configurations activate $config
  fi

}

gcloud-config
```
