# Executing the toy example


# To install LLVM 5.0.0 and clang-5.0 on ubuntu 16.04
sudo apt-get install llvm-5.0
sudo apt-get install clang-5.0
sudo apt-get install calng++-5.0

# Install cmake to build io_spec 
sudo apt-get install cmake

# Add following lines to ~/.bashrc and source it
export CXX="/usr/bin/clang-5.0"

# Run the following commands to create a symbolic link so your compiler can find opt,llvm-link and lli
sudo ln -s /usr/lib/llvm-5.0/bin/opt /usr/bin/opt
sudo ln -s /usr/lib/llvm-5.0/bin/llvm-link /usr/bin/llvm-link
sudo ln -s /usr/lib/llvm-5.0/bin/lli /usr/bin/lli

# Follow the readme in io_specialization to build the following projects in order
io_spec
file_lift
dtrace_gen

# Install dependencies for daikon
sudo apt-get install default-jre
sudo apt-get install default-jdk
sudo apt-get install graphviz
sudo apt-get install autotools-dev
sudo apt-get install automake
sudo apt-get install libz-dev
sudo apt-get install binutils-dev

# Install textinfo
wget http://ftp.gnu.org/gnu/texinfo/texinfo-6.8.tar.xz

# Untair it and then in the textinfo directory run
./configure --prefix=/usr/local/texinfo/6_6
make
sudo make install
sudo ln -s /usr/local/texinfo/6_6/bin/makeinfo /usr/local/bin/

# Download Daikon5.8.0
wget https://plse.cs.washington.edu/daikon/history/daikon-5.8.0/daikon-5.8.0.tar.gz
# Untar it in a directory as specified in daikon install docs and follow the process on the website. Before running make -C $DAIKONDIR rebuild-everything, Go to the file daikon-5.8.0/doc/Makefile and coment the following lines
${HTMLTOOLS}/html-add-favicon daikon ../daikon-favicon.png
#${HTMLTOOLS}/html-add-favicon developer ../daikon-favicon.png

# run the make -C $DAIKONDIR rebuild-everything command

# Change any reference to clang in io_spec.py to clang-5.0
# or setup an alias in your bashrc from calng to clang-5.0

# Uncomment the following line in io_spec.py
os.system("opt -load "+invdir+"/io_spec/build/proj/libiospec.so -iospec <"+app_bc+"> /dev/null")

# Run the toy example as specified in their given readme