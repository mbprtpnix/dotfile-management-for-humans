![dotfile-management-for-humans](https://user-images.githubusercontent.com/20260845/59078947-724fd680-88af-11e9-8457-465e2510460b.png)

## Starting From Scratch                                                        
                                                                                
### 🚦 A Quick Note About Workflows                                             
                                                                                
> To start from scratch, the remote repository you intend to use should be      
empty.If your remote repository is non-empty (even if the only contents are a   
single README file), then I recommend skipping to the                           
[Migrating to a New System](#migrating-to-a-new-system) section. The workflows  
are similar (and I promise you won't miss out on any important details), but in 
the migration section I cover how to deal with file conflicts; a topic not      
covered in this section since the remote repository is assumed to be empty.     
                                                                                
The first step to managing your dotfiles is to create a bare repository and     
establish an alias for working with it.                                         
                                                                                
```bash                                                                         
git init --bare $HOME/.dotfiles                                                 
alias dotfiles='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'      
```                                                                             
                                                                                
Next, hide untracked files and prevent adding the repository to itself.         
                                                                                
```bash                                                                         
dotfiles config --local status.showUntrackedFiles no                            
echo ".dotfiles" >> $HOME/.gitignore                                            
```                                                                             
                                                                                
Lastly, add a remote so that your local branch is tracked remotely.             
                                                                                
```bash                                                                         
dotfiles remote add origin <git-repo-url>                                       
```                                                                             
                                                                                
### 🍾 You're Done                                                              

Now your dotfiles repository is ready for use. I suggest adding the alias to    
your `.bashrc` file so that it is present for future session.  

## Using the Dotfiles Alias                                                              
                                                                                
We can demo the dotfiles alias by adding the `.gitignore` file we either created
or modified during the setup:                                                   
                                                                                
```bash                                                                         
dotfiles add .gitignore                                                         
dotfiles status                                                                 
dotfiles commit -m "Added gitignore."                                           
dotfiles push                                                                   
```                                                                             
                                                                                
Easy peasy 🍋 squeezy!  
