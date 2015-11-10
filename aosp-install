echo "----------------------------------------"
echo "Now updating system and installing jdk7"
echo "----------------------------------------"
sudo apt-get update
sudo apt-get install openjdk-7-jdk
echo "----------------------------------------"
echo "Installing required packages 14.0.4.3"
echo "----------------------------------------"
sudo apt-get install git-core gnupg flex bison gperf build-essential \
zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 \
lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev ccache \
libgl1-mesa-dev libxml2-utils xsltproc unzip
echo "----------------------------------------"
echo "Configuring USB access"
echo "----------------------------------------"
wget -S -O - http://source.android.com/source/51-android.rules | sed "s/<username>/$USER/" | sudo tee >/dev/null /etc/udev/rules.d/51-android.rules; sudo udevadm control --reload-rules
export OUT_DIR_COMMON_BASE=~/OUT
echo "----------------------------------------"
echo "Installing 'repo' for git"
echo "----------------------------------------"
mkdir ~/bin
PATH=~/bin:$PATH
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
echo "----------------------------------------"
echo "Initializing AOSP repo and checkout branch"
echo "----------------------------------------"
mkdir ~/WORKING_DIRECTORY
cd ~/WORKING_DIRECTORY
PS3='Please enter your choice: '
options=("4.2.2" "4.4.4" "5.0.1" "5.1.1" "Quit")
select opt in "${options[@]}"
do
    case $opt in
        "4.2.2")
            repo init -u https://android.googlesource.com/platform/manifest -b android-4.2.2_r1
            ;;
        "4.4.4")
            repo init -u https://android.googlesource.com/platform/manifest -b android-4.4.4_r1
            ;;
        "5.0.1")
            repo init -u https://android.googlesource.com/platform/manifest -b android-5.0.1_r1
            ;;
	"5.1.1")
            repo init -u https://android.googlesource.com/platform/manifest -b android-5.1.1_r9
            ;;
        "Quit")
            break
            ;;
        *) echo invalid option;;
    esac
done
echo "----------------------------------------"
echo "Syncing repo to working-folder"
echo "----------------------------------------"
repo sync
