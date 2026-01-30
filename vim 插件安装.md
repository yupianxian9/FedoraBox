# Vim插件安装

vim 下载：

```bash
sudo dnf install vim
```

在 `Vim` 中安装插件可以显著提升编辑效率，常见的插件管理器有 `Vim-plug`、`Pathogen` 和 `Vundle`。以下是使用 `Vim-plug` 安装插件的步骤和一些常用插件推荐。

### 使用 `Vim-plug` 安装插件

1. **安装 `Vim-plug`**：
   
   - 下载 `Vim-plug`：
     
     ```sh
     curl -fLo ~/.vim/autoload/plug.vim --create-dirs \https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
     ```

2. **配置 `.vimrc` 文件**：
   
   - 在 `~/.vimrc` 中添加插件配置。例如：
     
     ```vim
     set shiftwidth=4  " 使用 `>>`, `<<` 或自动缩进时的缩进量为4个空格
     set softtabstop=4 " 在编辑（如按退格键）时，将4个空格视为一个整体进行缩进
     
     
      call plug#begin('~/.vim/plugged')
      " 插件列表
      "Plug 'tpope/vim-fugitive'  " Git 集成
      Plug 'scrooloose/nerdtree' " 文件浏览器
      Plug 'vim-airline/vim-airline' " 状态栏增强
      "Plug 'vim-airline/vim-airline-themes' " 状态栏主题
      Plug 'ycm-core/YouCompleteMe' " 代码补全
      Plug 'scrooloose/syntastic' " 语法检查
      Plug 'tpope/vim-surround' " 快速编辑包围符号
      "Plug 'junegunn/fzf', { 'do': { -> fzf#install() } } " 模糊查找
      "Plug 'junegunn/fzf.vim' " fzf 集成
      Plug 'majutsushi/tagbar' " 代码结构浏览
      "Plug 'airblade/vim-gitgutter' " Git 差异显示
      Plug 'preservim/nerdcommenter' " 快速注释
      Plug 'sheerun/vim-polyglot' " 多语言语法高亮
     
      call plug#end()
     ```

3. - 打开 `Vim`，运行以下命令安装插件：
     
     ```vim
     :PlugInstall
     ```

4. **更新插件**：
   
   - 更新所有已安装插件：
     
     ```vim
     :PlugUpdate
     ```

5. **删除插件**：
   
   - 从 `.vimrc` 中移除插件配置后，运行以下命令清理：
     
     ```vim
     :PlugClean
     ```

### 常用插件推荐

1. **NERDTree**：
   
   - **功能**：文件浏览器，方便浏览和操作文件。
   
   - **安装**：
     
     ```vim
     Plug 'scrooloose/nerdtree'
     ```

2. **vim-airline**：
   
   - **功能**：状态栏增强，显示更多信息。
   
   - **安装**：
     
     ```vim
     Plug 'vim-airline/vim-airline'Plug 'vim-airline/vim-airline-themes'
     ```

3. **YouCompleteMe**：
   
   - **功能**：代码补全，支持多种语言。
   
   - **安装**：
     
     ```vim
     Plug 'ycm-core/YouCompleteMe'
     ```

4. **Syntastic**：
   
   - **功能**：语法检查，实时提示错误。
   
   - **安装**：
     
     ```vim
     Plug 'scrooloose/syntastic'
     ```

5. **vim-surround**：
   
   - **功能**：快速编辑包围符号（如引号、括号）。
   
   - **安装**：
     
     ```vim
     Plug 'tpope/vim-surround'
     ```

6. **fzf.vim**：
   
   - **功能**：模糊查找文件、内容等。
   
   - **安装**：
     
     ```vim
     Plug 'junegunn/fzf', { 'do': { -> fzf#install() } }Plug 'junegunn/fzf.vim'
     ```

7. **Tagbar**：
   
   - **功能**：代码结构浏览，显示函数、类等。
   
   - **安装**：
     
     ```vim
     Plug 'majutsushi/tagbar'
     ```

8. **vim-gitgutter**：
   
   - **功能**：显示 Git 差异（新增、修改、删除的行）。
   
   - **安装**：
     
     ```vim
     Plug 'airblade/vim-gitgutter'
     ```

9. **NERDCommenter**：
   
   - **功能**：快速注释代码。
   
   - **安装**：
     
     ```vim
     Plug 'preservim/nerdcommenter'
     ```

10. **vim-polyglot**：
    
    - **功能**：多语言语法高亮，支持多种编程语言。
    - **安装**：
    
    ```vim
    Plug 'sheerun/vim-polyglot'
    ```

### 总结

通过 `Vim-plug` 等插件管理器，可以轻松安装和管理 `Vim` 插件，显著提升编辑效率。常用插件如 `NERDTree`、`vim-airline`、`YouCompleteMe` 等，分别提供文件浏览、状态栏增强、代码补全等功能，满足不同需求。
